
# AWS EC2 and VPC Management Scripts

This repository contains two Python scripts to automate the creation and deletion of AWS EC2 instances and associated VPC resources using Boto3, the AWS SDK for Python. These scripts are property of DevOps Shack.

## Prerequisites

- Python 3.6 or higher
- Boto3 library
- AWS credentials configured (using `aws configure` or by setting environment variables)

## Scripts

1. **create_resources.py**
2. **destroy_resources.py**

### create_resources.py

This script creates a Virtual Private Cloud (VPC) and associated resources, including an Internet Gateway, a public subnet, a route table, a security group, and an EC2 instance.

#### Steps:

1. **Initialize a session using Amazon EC2**:
   Initializes Boto3 resource and client for interacting with EC2 service.

2. **Create a VPC**:
   Creates a VPC with a specified CIDR block.

3. **Enable DNS support for the VPC**:
   Enables DNS resolution and DNS hostnames for the VPC.

4. **Create and attach an Internet Gateway**:
   Creates an Internet Gateway and attaches it to the VPC.

5. **Create a public subnet**:
   Creates a public subnet within the VPC in the specified Availability Zone.

6. **Create a route table and a public route**:
   Creates a route table and adds a route to the internet via the Internet Gateway.

7. **Associate the route table with the subnet**:
   Associates the route table with the public subnet, making the subnet public.

8. **Create a security group**:
   Creates a security group within the VPC and authorizes ingress (inbound traffic) on ports 22 (SSH), 80 (HTTP), 443 (HTTPS), and a range from 3000 to 10000 (custom applications).

9. **Function to create EC2 instances**:
   Defines a function to create EC2 instances with specified configuration: AMI ID, instance type, key pair, network interface, tags, and placement in the specified Availability Zone.

10. **Create the instances**:
    Calls the function to create the specified number of instances and prints details of the created instances.

#### Usage:

```bash
python create_resources.py
