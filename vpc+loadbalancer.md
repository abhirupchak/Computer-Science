# AWS VPC and Load Balancer Setup Guide

## VPC Setup

### Step 1: Create a VPC
1. Go to **VPC** > **Your VPCs** > **Create VPC**.
2. Set:
   - **VPC Name**: `MyVPC`
   - **IPv4 CIDR Block**: `10.0.0.0/16`
3. Click **Create**.

### Step 2: Create Subnets
1. Go to **Subnets**.
2. For each subnet, click **Create Subnet** and specify:
   - **Subnet Name** (e.g., `S1-Private`, `S3-Public`).
   - **Availability Zone**.
   - **CIDR Block**:
     - `10.0.1.0/24` for Private Subnet 1.
     - `10.0.2.0/24` for Private Subnet 2.
     - `10.0.3.0/24` for Public Subnet 1.
     - `10.0.4.0/24` for Public Subnet 2.
3. Click **Create**.

### Step 3: Create and Attach an Internet Gateway
1. Go to **Internet Gateways** > **Create Internet Gateway**.
2. Name it (e.g., `MyInternetGateway`).
3. Click **Create**, select it, click **Actions**, then **Attach to VPC** and choose `MyVPC`.

### Step 4: Create and Attach a Virtual Private Gateway (Optional)
1. Go to **VPN Connections** > **Virtual Private Gateways**.
2. Click **Create Virtual Private Gateway** and name it (e.g., `MyVGW`).
3. Attach it to `MyVPC`.

### Step 5: Set Up Route Tables

1. **Create a Route Table for Public Subnets**:
   - Go to **Route Tables** > **Create Route Table**.
   - Name it (e.g., `PublicRouteTable`) and associate it with **MyVPC**.
   - Under **Routes**, add the following:
     - **Destination**: `0.0.0.0/0` (for Internet access)
     - **Target**: Select the Internet Gateway you created.
   - **Associations**: Attach this route table to the public subnets (`S3-Public` and `S4-Public`).

2. **Create a Route Table for Private Subnets**:
   - Go to **Route Tables** > **Create Route Table**.
   - Name it (e.g., `PrivateRouteTable`) and associate it with **MyVPC**.
   - Under **Routes**, add the following:
     - **Destination**: `192.168.0.0/16` (for internal access via VPN)
     - **Target**: Select the Virtual Private Gateway if you created one.
   - **Associations**: Attach this route table to the private subnets (`S1-Private` and `S2-Private`).



## Load Balancer Setup

### Step 1: Launch EC2 Instances
1. Go to **EC2** and launch two EC2 instances in different availability zones within the public subnets.
2. Attach a security group to allow inbound traffic (e.g., HTTP/HTTPS) from the load balancer.

### Step 2: Create a Target Group
1. In **EC2**, go to **Target Groups** > **Create Target Group**.
2. Set:
   - **Target Type**: Instances
   - **Name**: `MyTargetGroup`
   - **VPC**: `MyVPC`
3. Configure **Health Checks** (e.g., HTTP, ping path `/`).
4. Register your instances by selecting them, then click **Include as pending below** and **Create Target Group**.

### Step 3: Create an Application Load Balancer (ALB)
1. In **EC2**, go to **Load Balancers** > **Create Load Balancer** > **Application Load Balancer**.
2. Set:
   - **Name**: `MyALB`
   - **Scheme**: Internet-facing
   - **IP Address Type**: IPv4
3. Select the **VPC** and assign the ALB to two public subnets.

### Step 4: Configure Security Groups for the Load Balancer
1. Choose or create a security group for the load balancer to allow inbound HTTP/HTTPS traffic.
2. Attach the security group to the load balancer.

### Step 5: Set Up Listener and Routing
1. Configure a listener under **Listeners and Routing**:
   - Port **80** (HTTP) or **443** (HTTPS).
   - **Default Action**: Select `MyTargetGroup`.
2. Click **Create Load Balancer**.




