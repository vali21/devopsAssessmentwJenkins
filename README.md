# devopsAssessmentwJenkins

As prerequisites I have used Ubuntu 20.04 on Windows 10 on which I have installed ansible, python3, boto and jenkins.
For AWS, I have created a user with AdministratorAccess, downloaded the csv given at the end and created an ansible-vault file "cred.yml" containing:
aws_access_key: Access key ID
aws_secret_key: Secret access key
and encrypted with the password in "password.txt"

I have also created a key pair (.pem) and specified the path in the /etc/ansible/ansible.cfg file. 
![image](https://user-images.githubusercontent.com/49509610/161987613-993bc282-6465-4972-abe5-b0ae6671b5fd.png)

In the ansible playbook (main.yml) I have created tasks for: Creating a VPC, Creating an Internet Gateway, Creating a Subnet, Creating a Security Group, Creating Network ACLs, Creating Route Table, Creating the EC2 Instance, Adding new instance to the host group and specified the role for httpd which will deploy the html page.

First, I have tested the solution without using any CI/CD tools and it was successfull:
![image](https://user-images.githubusercontent.com/49509610/161988517-2c8cd4ad-73c7-4e31-8d1d-f90896ce8233.png)

Then I have created a pipeline in Jekins which you can find in the Jenkinsfile which has 2 stages. The first stage will fetch the code from github using an access token and the second stage will run the ansible playbook in the specified directory with the password.txt provided as an extra variable.

The output of the jenkins pipeline was successful:
![image](https://user-images.githubusercontent.com/49509610/161989647-13069e0b-56e6-497f-99c7-2d1c7175cac5.png)
and the instance was created:
![image](https://user-images.githubusercontent.com/49509610/161989773-dedf4e14-44a7-49e1-bb9b-b8af30068e4b.png)

By typing in the browser the public ip of the instance, we can see the webpage deployed successfuly.

![image](https://user-images.githubusercontent.com/49509610/161989934-a69b80e9-4b3f-48d5-949f-7d5510cd44d7.png)
