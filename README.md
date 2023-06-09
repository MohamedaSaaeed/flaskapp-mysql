## DevOps BootCamp Capstone Project
* The project involves deploying a Flask application and MySQL database on AWS infrastructure built using Terraform. The infrastructure includes an EKS cluster, Full network, and ECR.
* Once the infrastructure is set up, Ansible is used to install and configure Jenkins on an EC2 instance. Jenkins is then used to create a pipeline for the Flask application, which includes building the application, testing it, and deploying it to the EKS cluster using Kubernetes.
* The application's code is stored in a Git repository, and Jenkins is configured to pullthe code from the repository and run the pipeline automatically whenever there is a new commit.
<img src=https://user-images.githubusercontent.com/116665263/227786542-2b8fc3a4-b8d9-4348-97c8-a29d3a1263f3.png>

## Author
##### Name: Mohamed Ahmed Saaeed
##### Email: mohamedasaaeed@gmail.com
## Technologies
* [Terraform](https://developer.hashicorp.com/terraform/downloads)
* [Ansible](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-centos-7)
* [Docker](https://docs.docker.com/engine/install/centos/) 
* [Python 3.6](https://www.rosehosting.com/blog/how-to-install-python-3-6-4-on-centos-7/)

## Installation and Running

### 1- Using Terraform to build our infrastructure.
We need to build our network, EC2 instance, EKS cluster of two nodes, and ECR.
```bash
cd /Terraform
```
```bash
terraform init
```
```bash
terraform apply
```
```bash
cp tfkey.pem ../ansible
```
### 2- Using Ansible to install and configure Jenkins on our EC2 instance.
Change the permissions of the key pair.
```bash
cd /ansible
```
```bash
chmod 400 tfkey.pem
```
```bash
# First, add the 'instance public ip' to the inventory file using the vim editor.
# Second, run the below command
ansible-playbook -i 'instance public ip', -u ubuntu --private-key ./tfkey.pem playbook.yaml
``` 
### 3- Manually, 
* Connect to the EC2 instance to unlock Jenkins 
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
* Install the necessary plugins and create an account.  
* Create my pipeline called [FlaskApp-MySQL-Pipeline].
* From Manage plugins, install Cloud AWS credentials.
* From Manage credentials, add AWS credentials with access-key and secret key called [Terraform]
<img src=https://user-images.githubusercontent.com/116665263/226451947-67197967-a76c-4322-a373-ad945314ea5d.PNG>
* Configure the pipeline by choose Github project by adding URL link.
<img src=https://user-images.githubusercontent.com/116665263/226452679-acfc5213-eb8a-4444-951a-ec6ae04beb48.PNG>
* Build the pipeline script from SCM.
<img src=https://user-images.githubusercontent.com/116665263/226451426-fbb3b8d8-1b11-42bf-bc5b-6686b0720855.PNG>
* Get the DNS name of load balancer and put it in the browser
<img src=https://user-images.githubusercontent.com/116665263/226451013-c5d4c91c-6000-4fc5-a686-437678ddfeb1.PNG>