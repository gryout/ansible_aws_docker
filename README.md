# ansible_aws_docker

This project creates an EC2 instance from an ubuntu image, deploys nginx, php-fpm containers and creates auto scaling group by using the previously created EC2 instance's image. 

Tested on Ubuntu 18.04.2 

Requirements:
  - ansible 2.7.1
  - python3
  - boto
  - botocore
  - boto3
  
  

**Before running the playbook make sure you have a keypair and your aws access keys.**

1. Modify "keypair" "vpcid" "localsubnet" variables in group_vars/all.yml according to your AWS environment.
2. Modify "private_key_file" in ansible.conf with location of your pem file.
3. Create an encrypted ./awsKeys.yml file with ansible-vault and add your AWS keys to ami_access ami_secret variables respectively. You can use below command to create the awsKeys.yml file and give it a password.

```ansible-vault create awsKeys.yml```

awsKeys.yml file should look like below:

```
ami_access: 123123
ami_secret: 123asd21
```

**Running the playbok**

``` ansible-playbook --ask-vault-pass deploy.yml  ```  

The playbook will print out the ELB public dns once finished.
