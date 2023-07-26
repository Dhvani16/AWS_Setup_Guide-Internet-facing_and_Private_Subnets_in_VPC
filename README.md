# AWS_Setup_Guide-Internet-facing_and_Private_Subnets_in_VPC
**Introduction**
  This guide provides step-by-step instructions to create an AWS infrastructure with an internet-facing subnet and a private subnet within a Virtual Private Cloud (VPC). The architecture includes two Linux servers, one in each subnet, accessible via SSH.

**Prerequisites**
Before you begin, ensure you have the following:
1. An AWS account with appropriate permissions to create resources.
2. AWS Command Line Interface (CLI) installed (optional but recommended).

**IAM Setup**
1. Create a new IAM group with relevant permissions for the tasks.
2. Create a new IAM user and add the user to the group created in the previous step.

**AWS Infrastructure Setup**

**1. VPC Creation**
    1. Navigate to the AWS Management Console.
    2. Go to the VPC Dashboard and click on "Create VPC".
    3. Provide the required details for VPC creation:
         1. VPC name: [Your VPC Name]
         2. IPv4 CIDR block: [Your VPC IPv4 CIDR Block (e.g., 10.0.0.0/16)]
         3. IPv6 CIDR block (optional): [Your VPC IPv6 CIDR Block]
    4. Click "Create VPC."
    
**2. Internet-facing Subnet**
    1. Go to the Subnets section in the VPC Dashboard.
    2. Click on "Create subnet."
    3. Provide the following details:
        1. Subnet name: [Your Internet-facing Subnet Name]
        2. VPC: [Select the VPC created in the previous step]
        3. Availability Zone: [Select an Availability Zone different from the private subnet]
        4. IPv4 CIDR block: [Your Internet-facing Subnet IPv4 CIDR Block (e.g., 10.0.1.0/24)]
    4. Click "Create subnet."
    
**3. Private Subnet**
    1. Follow the same steps as for the Internet-facing subnet but choose a different Availability Zone.
    2. Use a different IPv4 CIDR block for the private subnet (e.g., 10.0.2.0/24).

**4. Launch EC2 Instances**
    1. Go to the EC2 Dashboard and click on "Launch Instance."
    2. Select an Amazon Machine Image (AMI) for your Linux server (e.g., Ubuntu).
    3. Choose an instance type "t2.micro" to stay within the free tier.
    4. Configure the instance:
        1. Network: [Select the VPC you created]
        2. Subnet: [Choose the Internet-facing subnet]
        3. Auto-assign Public IP: [Enable]
    5. Add storage, tags, and configure security groups as required.
    6. Review the instance details and launch it.

**5. Connect to Instances via SSH**
    1. Obtain the public IP address of the Internet-facing server from the EC2 Dashboard.
    2. Use SSH to connect to the Internet-facing server:
      ssh -i /path/to/your/private/key.pem ec2-user@internet_facing_server_ip
    3. Once connected to the Internet-facing server, SSH into the private server using its private IP address:
      ssh -i /path/to/your/private/key.pem ec2-user@private_server_private_ip

**Conclusion**
  Congratulations! You have successfully set up an AWS infrastructure with two subnets (one internet-facing and one private) within a VPC. You can now access both Linux servers via SSH.
  Please refer to the provided PDF with screenshots for visual guidance during the setup process.


  Feel free to adjust the instructions according to your setup and include any additional information that might be helpful to users. Make sure to replace [Your VPC Name], [Your VPC IPv4 CIDR Block], and other placeholders with the actual values from your setup. Additionally, include any details about IAM permissions given to the group and any other configurations you made during the setup process.
