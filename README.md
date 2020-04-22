# Node Cookbook AMI :monkey: :cyclone:
This repository will show you how to automate AMI for Nodejs in AWS.

Packer is an open source tool for creating identical machine images for multiple platforms from a configuration management tool such as Chef which is what is used in this repository. These machine images will have a pre-configured operating system and already installed software which can be used to make machines.

#### Benefits of Packer
- Super fast infrastructure deployment
- Multi-provider portability
- Improved stability
- Greater testability

### Pre-requisites
- packer
- Chef
- Git
- AWS account

## Steps
The steps below will show you how to set up this AMI, please ensure you cloned the repo and navigate to your folder called 'NodeCookbook-packer' within your terminal.

After you have done that, please follow the commands below.

##### Pull Cookbook
First we will need to pulls the cookbook from the git repository:
```
$ berks vendor
```

#### Configure packer file
Now you must configure the packer file so that the credentials are set to your account, the changes you will need to make are shown below:
```
"aws_access_key": "{{env `<YOUR ENVIRONMENT VARIABLE for your AWS access key>`}}"
"aws_secret_key": "{{env `<YOUR ENVIRONMENT VARIABLE for your AWS secret access key>`}}"
```
then you will have to change the subnet to you subnet id:
```
"subnet_id": "<subnet-0e9b6138ff1ce18f2>"
```
lastly you will need to change the key pair you used to connect to AWS.
```
"ssh_keypair_name": "<Name of your key used pem key used to connect to AWS>"
"ssh_private_key_file": "<Path of your pem key, eg.~/.ssh/name_of_key.pem>"
```
then check if the packer file is verified so that it will cause no errors when ran:
```
$ packer validate packer.json
```
##### Build AMI
Now we can build the AMI in AWS:
```
$ packer build packer.json
```

If you have followed all these steps you should have an AMI in you AWS.

## Authors

**Mahan Jahromi** - *DevOps Engineer* - [Mahansparta](https://github.com/Mahansparta)

#### Acknowledgments

* Hat tip to anyone whose helped me with this Project
* Inspiration  - Filipe Paiva
