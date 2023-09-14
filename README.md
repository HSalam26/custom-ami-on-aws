# Create Custom AMI on AWS

This guide will walk you through the process of creating a custom Amazon Machine Image (AMI) on AWS. Custom AMIs are useful for preserving your configured instances or creating a consistent environment for future instances.

## Prerequisites

Before you begin, ensure you have:

- An AWS account.
- AWS CLI configured (for optional additional tasks).

## Step-by-Step Guide

1. **Access EC2 in AWS Management Console**
   - Log in to the AWS Management Console.
   - Navigate to the EC2 service.

2. **Launch an EC2 Instance**
   - Launch a new EC2 instance with the desired operating system and configuration.
   - Specify a name for your instance.

3. **Choose an Existing Key Pair or Create a New One**
   - During instance creation, choose an existing key pair or create a new one. This key pair will be used for SSH access.

4. **Launch the Instance**
   - Complete the instance launch process.

5. **Connect to the EC2 Instance**
   - Use a tool like Putty to connect to your EC2 instance using the public IP and the key pair you selected or created.

6. **Log In as Root User**
   - After connecting via SSH, log in as the root user using the following command:
     ```
     sudo su
     ```

7. **Update the System**
   - Update the system packages using the following command:
     ```
     yum update -y
     ```

8. **Install Nginx**
   - Install Nginx using the Amazon Linux Extras repository:
     ```
     sudo amazon-linux-extras install nginx1
     ```

9. **Start Nginx Service**
   - Start the Nginx service:
     ```
     systemctl start nginx.service
     ```

10. **Check Nginx Service Status**
    - Verify the status of the Nginx service:
      ```
      systemctl status nginx.service
      ```

11. **Create an AMI**
    - In the AWS Management Console, select the instance you want to create an image from.
    - Go to "Actions," then "Image and Templates," and choose "Create Image."
    - Provide a name for your custom AMI.

12. **Confirm Image Creation**
    - Select "Create Image" to initiate the image creation process.

13. **Verify Image Creation**
    - To confirm that the image has been created, go to the "AMI" section in the AWS Management Console.

14. **Test the AMI**
    - Launch a new EC2 instance using the custom AMI you created.
    - Connect to the new instance using SSH (Putty) and check if Nginx is installed:
      ```
      sudo systemctl status nginx.service
      ```

15. **Final Check**
    - You should receive a message indicating that Nginx is inactive, as it was installed but not started.

That's it! You've successfully created a custom AMI on AWS. This AMI can be used to launch new instances with your desired configuration in the future.
