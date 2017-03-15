# Devops Lesson 1 Bonus Lab

## Overview

This bonus exercise is designed to give some background into networking which is essential for DevOps.


### Step 1

Log into the Google Cloud Console.  
`https://console.cloud.google.com`  

Start your virtual machine if it isn't already running.

_Click the SSH button_ at the right hand side of the line of information about your lab computer.
This will open a new browser window with a terminal connection. Find the icon that looks like a gear
in the upper right hand corner of this terminal browser window and select _Change Linux User Name_.
Enter _student_ and _click Change_. Now notice the prompt that says "student@lab:~$"

It is important that you do this for all other exercises.

### Step 2

Check what network interfaces are running.  
`/sbin/ifconfig`  
_lo_ with IP 127.0.0.1 is the loopback interface to talk to services on the current machine.  
_eth0_ is the primary ethernet connections. It's IP address starts with 10 which means it can only be accessed on the current LAN. It is internal to Google.  
_docker0_ is the interface used by the virtualisation tool Docker to communicate with
containers on this machine.  

### Step 3

Check the IP to host name mappings.  
`cat /etc/hosts`  
See that your machine has a hostname based on its name and project.  

Find the IP address of the DNS server.  
`cat /etc/resolv.conf`  

### Step 3

Find out which network services are running. Port 22 is SSH.  
`netstat -an | grep LISTEN`  

### Step 4

We need to change the Docker startup script so that it listens on TCP port
2375.  
`sudo vi /etc/systemd/system/multi*/docker.service`  
Add a second -H switch the the ExecStart line so that it reads:  
`ExecStart=/usr/bin/dockerd -H fd:// -H tcp://0.0.0.0:2375`  
Reload the daemon processes.  
`sudo systemctl daemon-reload`  
Restart Docker.  
`sudo systemctl restart docker`  
Check that there is a listener on port 2375:  
`netstat -an | grep 2375`  

### Step 5

Telnet is an old tool for opening remote terminal sessions. It is no longer used in
favour of SSH. However, telnet can communicate on any network port. It is now a _vital_
DevOps tool. We will use it to communicate with Docker using its web interface.

Install telnet.  
`sudo apt-get install telnet`  
Connect to Docker using telnet:  
`telnet localhost 2375` 
Now type the following two HTTP headers then hit enter twice.  
`GET /events HTTP/1.1`  
`Host: localhost`  
You should see a response from Docker.  
Exit telnet by typing control-] followed by quit.  


### Step 6

Stopping your lab computer.

Close the SSH window.  
`exit`

You will want to stop the lab computer at the end of each day to prevent it from accumulating costs during the evening and night.

From the Web UI you can navigate to the Compute Engine section and select your lab computer. When it is selected click on the icon representing the "Stop" operation.


