# Deploying a Web Application Using Apache HTTPD on Cloud (AWS EC2 Instance)

This project demonstrates how to host a web application written in HTML using the Apache HTTPD server on an AWS EC2 instance.

## Setting up the Project Environment

### Initializing EC2 Instance

1. Log into the AWS Console using your IAM user account.
2. Create an EC2 instance and select an OS image — **Ubuntu**.
3. Create a new key pair with any name and download the `.pem` file.
4. Use the same key pair when configuring your EC2 instance.
5. Instance Type: **t2.micro** (eligible for the AWS Free Tier).
6. Connect to the EC2 instance using SSH.

### Connecting to the Instance Using SSH

Ensure you're in the directory where your key pair file is located, then run:
```bash
chmod 400 "keypair_name.pem"
```
After setting the permissions, use the following command to SSH into your EC2 instance:
```bash
ssh -i <keypair_name>.pem ubuntu@<IP_ADDRESS>
```

### Configuring Ubuntu on the EC2 Instance and Installing Dependencies
```bash
sudo apt update
sudo apt install git
```

### Installing Apache HTTPD
```bash
sudo apt install apache2
sudo systemctl start apache2
```

### Cloning the Source Code into the Ubuntu EC2 Instance
```bash
git clone https://github.com/Akshata0211/AWSDemo.git
```
This will download all the contents of the repository AWSDemo and store it in the EC2 instance's current working directory.

### Hosting the Application Using Apache
To host the application, copy the contents of the cloned repository into the Apache HTML folder:
```bash
cp -r . /var/www/html
```
### Accessing the Application
Apache listens on port 80. You can access the application using the following URL:
```bash
http://<ec2-instance-public-ip>
```
If the service is not running, start the service.

If the security group is not allowing inbound http traffic, go to the inbound rules in the security group and allow http traffic.
