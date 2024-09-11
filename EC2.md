# Steps to Use EC2 on AWS

Amazon EC2 (Elastic Compute Cloud) on AWS (Amazon Web Services) is a service that provides scalable computing capacity in the cloud. It allows users to rent virtual servers (referred to as EC2 instances) to run applications, perform tasks, or host websites. With EC2, users can easily scale computing resources up or down based on their needs, paying only for the capacity they use.

---

## Table of Contents

- [Creating AWS Account](#creating-aws-account)  
- [Using EC2](#using-ec2)
- [Downloading PuTTY](#downloading-putty)
- [Using PuTTY Terminal](#using-putty-terminal)

---

## Creating AWS Account

To get started with AWS and EC2, create an AWS account after clicking sign up on the aws website.

---

## Using EC2

Now that you have an AWS account, you can set up an EC2 instance:

1. Log in to AWS and navigate to the **EC2 Dashboard**.
2. Click on Launch Instance to create a new virtual machine using ubuntu OS option on the aws console.
3. Name your file.
4. - Allow **SSH (port 22)** to connect via PuTTY.
   - Allow **HTTP (port 80)** to host the website.
6. Launch and Create Key Pair: Download the `.ppk` file for later use in PuTTY.

---

## Downloading PuTTY

PuTTY is an SSH client you will use to connect to your EC2 instance. To download and set it up:

1. Download **PuTTY** from [the official website](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).

---

## Using PuTTY Terminal

After downloading PuTTY follow these steps


   
2. **Open PuTTY**:
   - Enter the Public IP of your EC2 instance in the **Host Name** field.
   - Under **SSH -> Auth**, browse to the `.ppk` file.
   
3. **Login to EC2**:
   - Click **Open** to start the session.
   - When prompted, log in as `ubuntu`.

---

## Hosting a Simple HTML Website

1. Now enter these series of commands on the Linux terminal:
   
       sudo su                  #switches to root user
       apt update               #to update the system
       apt install apache2      #to install apache2 Apache2 (or simply Apache) serves as the web server software that delivers the HTML content to users' browsers.
       cd /var/www/html         #to change the working directory to html folder/directory
       rm index.html            #to remove the original index file present in html folder
       vi index.html            #to use vim editor to create a new index.html file
   
2. On the Vim terminal follow these steps:
   - Press i to enter insert mode
   - Make the html file
   - Press ctrl+c and type :wq(write quit)
3. Now load the public ip address and you should have a website containing 'hi'
   
       
       
   



