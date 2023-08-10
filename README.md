# aws-devops-projects
This repo includes aws services and devops projects.

![image](https://github.com/lakshmir2023/aws-devops-projects/assets/141936877/353df2dc-2003-48f9-a87c-83d4a8ee1185)

Project: Create a VPC and deploy two applications in different availability zones. Also create a load balancer to balance the load between the instances automatically.

Software pre-requisite:
Visual Studio Code

Hands-on:
Connect the EC2 instance.
$ sudo su

Want to install terraform in the instance
Browse terraform download and copy the linux command link and run it on the terminal

#wget https://releases.hashicorp.com/terraform/1.5.0/terraform_1.5.0_linux_amd64.zip

#wget – used to download the file from the URL

#ls –lrt

#apt install unzip

#unzip terraform_1.5.0_linux_amd64.zip

#ls –lrt

#mv terraform /usr/local/bin/

#terraform --version

Our code creates VPC, EC2 instances, Load Balancers, S3 buckets. For that it requires to assign permissions to our instance. We are going to add roles for temporary access.

IAM Roles  Create role  EC2 service. Add Permissions: AmazonVPCFullAccess, AmazonEC2FullAccess, AmazonS3FullAccess.
Rolename: terraform-new-role  create role
Attach the role in the ec2 instance.
EC2 instance  actions – security – modify iam role  terraform-new-role  save it.

Open visual Studio Code
Download extensions (add-ons) : open extension tab  browse terraform  install anton kulikov’s extension

Open a new folder and add files provider.tf, main.tf, variables.tf, userdata.sh, userdata1.sh

AWS Terraform documentation
https://registry.terraform.io/providers/hashicorp/aws/latest/docs

After writing the code follow these steps:

To initialize the environment
#terraform init
Lists the infrastructure to create
#terraform plan
Will automatically create our infrastructure in the specified region.
#terraform apply
#ls - lrt
we can see the terraform statefile – it is the brain or memory of the terraform.
#cat terraform.tfstate

Terraform is immutable – means if you do some changes in the code and runs the code it will delete the existing infrastructure and create the new infrastructure. It won’t edit in existing infrastructure.

If you edit manually the security group then run the below command
#terraform refresh 
It will refresh the state file.

To destroy the infrastructure
#terraform destroy --auto-approve

or

#terraform destroy

the above command will automatically destroy the resources.
