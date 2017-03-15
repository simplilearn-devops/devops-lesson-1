# Devops Lab 1.1 Cloud Setup

These instructions will guide you to create an identity with Google, set up a 
billing account, and create your devops project.

## Overview

In this lab you sign up for the Google Cloud free trail. To confirm your identity
you must have a credit card or debit card (a pre-paid credit card will not work)
to register for the free trial.

Note that Goggle may debit $1 from your card for validation purposes. If
they do this it will be refunded immediately.


### What you need

To complete this lab, you need:

* Internet access
* Access to a supported Internet browser
* A credit card or debit card to register for the free trial

The following browsers are known to work: 
* The latest version of Google Chrome, Firefox, or Microsoft Edge
* Microsoft Internet Explorer 11+
* Safari 8+ (Safari private mode is not supported)


### What you learn

When you complete this exercise you will have an account
on the Google Cloud Platform and a project ready for the 
DevOps course.

## Introduction

In this lab you register for the Google Cloud Platform free trial. The free trial provides you:

* $300 Credit for Free

Sign up and get $300 to spend on Google Cloud Platform over the next year and discover the power of the GCP products.

* You will not be billed
 

When you sign up for the free trial, you are asked to provide your credit card 
information. 
This information is used only to verify your identity and let us know you're not a 
robot. 
Your credit card is not charged during or after your free trial unless you 
upgrade to a paid account.

## Register for the free trial

To register for the free trial:

### Step 1

Open the free trial registration page:

https://console.cloud.google.com/freetrial


### Step 2

If you do not have a Gmail account, follow the steps to create one. 
Otherwise, log in and proceed to the next step

### Step 3


Complete the registration form.


### Step 4


Read and agree to the terms of service.

### Step 5


Click __Accept and start free trial__

### Step 6

Click on the three horizontal bars at the left most side of the blue bar near the top 
of the browser window. This will cause a tray to slide out from the left.
In this tray _click on Billing_. Next refresh the browser window and this action
will reveal a blue button in the upper right hand corner with the name "UPGRADE".
_Click on the UPGRADE button_ and confirm in the dialog box.


## Create the DevOps Project

Follow these steps to create a Google Cloud Platform project named 'devops'
for this course.

### Step 1 

Open the Cloud Platform Console at https://console.cloud.google.com  and
click __Select a project > Create a project__

### Step 2

In the 'New Project' dialog:

* For __Project name__, type __DevOps__
* In you have configured multiple billing accounts, for __Billing account__, select your preferred account.
* Click __Create__


## Create your lab computer

You will now create a Compute Engine instance that will be your own computer
in the cloud for performing all the work during this course.

### Step 1

Click on the three horizontal bars at the left most side of the blue bar near the top
of the browser window. _Select Compute Engine_. Be patient and wait until Google initializes
this area of the Google Cloud Platform for you.

### Step 2

_Click on first icon to the right of the search area in the blue bar_. If you hover over this
icon you will see the hint Activate Google Cloud Shell. _Click this icon_ and notice a terminal
is opened at the bottom of the browser window.

### Step 3

In the Google Cloud Shell window wait until you see the prompt displayed. 

We are going to copy an image from a bucket. We first need to create a bucket.
We need to create a unique identifier, so type the following command replacing
xyz with your initials and replacing 20170119 with todays's date.  
`gsutil mb gs://devops-xyz-20170119`  

Now we need to copy files from a bucket in another project to the new bucket.
Type the following command again substituting your initials and today's date.
This can take a few minutes.  
`gsutil cp gs://simplilearn-devops-image/*2017*gz gs://devops-xyz-20170119/`  

Verify that the copy worked, again substituting your initials and today's
date.  
`gsutil ls`  
`gsutil ls gs://devops-xyz-20170119/`  

Close the shell.  
`exit`

### Step 4

Select _Images_ from the left column. A list of images will appear.  

We need to create an image to create a computer. Select _CREATE IMAGE_ at
the top of the page.
Enter Name `student-image`  
Leave Family and Description blank.  
Change Source to _Cloud Storage file_  
Hit _Browse_ and you will see your bucket. Hit the arrow to the right of
the bucket and you will see the two files. Select the latest one ending
`20170108.tar.gz`.  
Hit _Select_.

Now create an image from the file by hitting _Create_. It may take a few
minutes. The new image should appear at the top of the list of images.

### Step 5

We are now going to create a computer from the image.

Select _VM Instances_ from the left hand column.
Select _Create Instance_.

Give it a Name `lab`  
Select a Zone near to where you are located.  
See that it tells you the Effective hourly rate and the estimated monthly
cost. This cost will barely impact your $300 credit.

Choose how many CPUs and how much memory you want. The default is sufficient.
Note that more CPUs and more memory increase the cost.

We need to specify a boot disk. Select _Change_. You will see a list of OS
images. Select the _Custom images_ tab.

Need to define the _Boot disk type_. Select _SSD persistent disk_ and give
it a _Size_ of 200. Select _Select_.

Now create it by hitting _Create_ at the bottom of the screen. It will take
aa few minutes.

You should see the VM Instance. Note that it is running.

### Step 6 

_Click the SSH button_ at the right hand side of the line of information about your new lab computer.
This will open a new browser window with a terminal connection. Find the icon that looks like a gear
in the upper right hand corner of this terminal browser window and select _Change Linux User Name_.
Enter _student_ and _click Change_. Now notice the prompt that says "student@lab:~$"

You now have a working computer for conducting all class work for the DevOps Practitioner course.

See what is install. Explore the machine.  
`ls -l`  

### Step 7

We will need the build tool Maven for later exercises. We will now install
Maven. We need to be root, so we will use `sudo`.  
`sudo apt-get update`  
`sudo apt-get install maven`  
You will see a long list of dependencies.  
Enter `Y` to accept them.

Maven will get installed.

Check the versions of Java and Maven which are installed.  
`java -version`  
`mvn -v`  

### Step 8

Stopping your lab computer.

Close the SSH window.  
`exit`

You will want to stop the lab computer at the end of each day to prevent it from accumulating
costs during the evening and night.

From the Web UI you can navigate to the Compute Engine section and select your lab computer. When it
is selected click on the icon representing the "Stop" operation.


