# Devops Lab 1.1 Cloud Setup

These instructions will guide you to create an identity with Google, set up a 
billing account, and create your devops project.

## Overview

In this lab you sign up for the Google Cloud free trail. To confirm your identity
you must have a credit card or debit card (a pre-paid credit card will not work)
to register for the free trial.


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

Sign up and get $300 to spend on Google Cloud Platform over the next 60 days and discover the power of the GCP products.

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

_Click on first icon to the right of the search area in the blue bar. If you hover over this
icon you will see the hint Activate Google Cloud Shell. _Click this icon_ and notice a terminal
is opened at the bottom of the browser window.

### Step 3

In the Google Cloud Shell window wait until you see the prompt displayed. Then click into this
area and type the following:

gcloud compute instances create lab --machine-type n1-standard-2 --zone us-central1-b --image debian-8-student-gui-v20161130 --image-project simplilearn-devops

### Step 4

Close the Google Cloud Shell window and refresh the browser page so that you see an entry
for your lab computer.

### Step 5 

_Click the SSH button_ at the right hand side of the line of information about your new lab computer.
This will open a new browser window with a termain connection. Find the icon that looks like a gear
in the upper right hand corner of this terminal browser window and select _Change Linux User Name_.
Enter _student_ and _click Change_. Now notice the prompt that says "student@lab:~$"

You now have a working computer for conducting all class work for the DevOps Practioner course.
