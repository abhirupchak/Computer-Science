# How to Run a Docker Container Using Nginx

<h2>This tutorial will tell you how to host a simple hi webpage on nginx using a docker container</h2>

---

# Launching an EC2 Instance and Connecting via PuTTY

## Step 1: Log In to AWS
1. Log in to your [AWS Management Console](https://aws.amazon.com/console/).

## Step 2: Open the EC2 Dashboard
1. In the AWS Management Console, search for **EC2** in the search bar.
2. Click on **EC2 Dashboard**.

## Step 3: Launch a New EC2 Instance
1. In the EC2 Dashboard, click **Launch Instance**.
2. Provide a name for your instance.

## Step 4: Choose an Amazon Machine Image (AMI)
1. Select an **Amazon Machine Image (AMI)**. For example, select **Ubuntu Server**.

## Step 5: Configure the Key Pair (Login)
1. In the **Key Pair (login)** section, click on **Create new key pair**.
2. Enter a **Key pair name**.
3. Choose **RSA** as the key pair type.
4. For **Private key file format**, select **.ppk** (for PuTTY).
5. Click **Create key pair**.
## Step 6: Configure the Security Group
1. Scroll to the **Configure Security Group** section.
2. Set the inbound rules as follows:
   - **SSH** (port 22)
   - **HTTP** (port 80)
## Step 7: Launch the Instance
1. Click **Launch**.

---

# Connecting to Your EC2 Instance via PuTTY

## Step 1: Open PuTTY
1. Open the **PuTTY** application on your computer.

## Step 2: Configure PuTTY
1. In the **Host Name** field, enter the **public IP address** of your EC2 instance.
2. In the left-hand side panel, click on **SSH** and click on **Auth**.
3. Under **Private key file for authentication**, click **Browse**.
4. Select the .ppk file you downloaded earlier.

## Step 3: Connect to the EC2 Instance
1. Click **Open** to initiate the connection.
2. If prompted with a security alert, click **Yes** to accept.
3. Login with **ubuntu**.
   
# Installing Docker 

## Run these series of commands 

    sudo apt update
    sudo apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    jq

    curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash

  Docker has been installed now.

# Pull Nginx Image from Dockerhub and Use it to run container

## Step 1: Pull Nginx and run a container named docker-nginx
 Run the following command(always use sudo in front of commands using docker)
   
       docker pull nginx
       docker run --name docker-nginx -p 80:80 nginx

## Step 2: Try loading the public IP address
 Try loading the ip address but remove the  https:// part from the address you should be able to view the default nginx web server page.
 In your terminal, enter CTRL+C to stop the container from running as it is currently attached to your terminal.
     
## Step 3: Remove the container
Enter the following command to remove the container as docker cannot run multiple docker containers using the same image.

     docker rm docker-nginx
## Step 4: Building a Web Page to Serve on Nginx
Create a new directory for your website content within the home directory:

    mkdir -p ~/docker-nginx/html
Navigate into to it by running this command:

    cd ~/docker-nginx/html
Create an HTML file to serve on your server:

    vim index.html
Press i to enter insert mode and insert this html content:

    <html>
      HI
    </html>
Now press Shift and type :wq and press enter to exit.

## Step 5 — Linking the Container to the Local Filesystem:
To do this, use the -v flag to map the ~/docker-nginx/html folder from your server to a relative path in the container/usr/share/nginx/html with this command:

    docker run --name docker-nginx -p 80:80 -d -v ~/docker-nginx/html:/usr/share/nginx/html nginx
## Step 6 - Now load the Public IP again:
Again remove the https:// part from the address and you should be able to see the HI html webpage.





 

