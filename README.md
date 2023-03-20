# DevOps BootCamp Capstone Project

This Capstone project is a Project for building, pushing, and deploying a flask app with MySQL database on ECR and EKS.
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
* Install the necessary plugins and create an account.  
* Create my pipeline.
* From Manage plugins, install Cloud AWS credentials.
* From Manage credentials, add AWS credentials with access-key and secret key called [Terraform]
* Configure the pipeline by adding Github URL link.
* Build the pipeline.





 
## Usage

```python
import foobar

# returns 'words'
foobar.pluralize('word')

# returns 'geese'
foobar.pluralize('goose')

# returns 'phenomenon'
foobar.singularize('phenomena')
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)