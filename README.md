 # SETTING UP A SCALABLE FILE STORAGE SYSTEM USING AMAZON ELASTIC FILE SYSTEM
  ## AIM
       To  setting up a scalable file storage system using Amazon Elastic File System (EFS) for two EC2 instances in different availability zones. 
## PROBLEM STATEMENT
  This experiment demonstrates how to configure Amazon EFS to provide a shared storage solution for two Linux EC2 instances across different availability zones, enabling easy data sharing. The aim is to ensure both instances can mount and access the EFS file system and validate data consistency across instances.

## ALGORITHM
Steps 1: Create two EC2 instances in different availability zones.
Go to the EC2 service in the AWS Management Console.

Launch two Linux-based EC2 instances (e.g., Amazon Linux 2) and place them in different availability zones within the same VPC.

Assign each instance a security group that allows NFS access on port 2049.

Steps 2: Set up a security group that allows necessary communication between the instances and EFS.
Create or configure a security group that allows inbound NFS traffic on port 2049 from the security group of both EC2 instances.

Attach this security group to the EFS file system to permit access from both instances.

Steps 3: Create an EFS file system and mount it to both EC2 instances.
In the AWS Console, navigate to the EFS service and select Create file system.

Select the same VPC as your EC2 instances and configure mount targets in the availability zones where your instances are located.

Complete the setup and take note of the file system ID (e.g., fs-064645ac116a12816).

Steps 4: Ensure that the EC2 instances can access the file system and share data between them.

## COMMANDS
EC2 INSTANCE 2
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
vi file  # Create a file and add some text
```
EC2 INSTANCE 1
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
ls
cat file
```

## OUTPUT
![image](https://github.com/user-attachments/assets/61bd0688-b660-4f5d-b8a7-f53510eb70c6)

![image](https://github.com/user-attachments/assets/22335f4a-2752-4401-8cbd-d77046a1982f)

![image](https://github.com/user-attachments/assets/71258169-d86c-412f-8079-c81f2fe34f6e)

![image](https://github.com/user-attachments/assets/24b33d1b-0e5d-43c5-904c-718fa6d9e7e1)

![image](https://github.com/user-attachments/assets/a14963a7-48df-4e54-82e1-b87d78c36b34)

![image](https://github.com/user-attachments/assets/3fd5576b-7518-47f0-9721-859ae2bbd6c9)

### REG NUMBER:212223040157
### NAME:PRIYANGHA G

## RESULT
Successfully set up a scalable file storage system using Amazon EFS shared between two Linux EC2 instances in different availability zones, enabling consistent data sharing.
 

  


