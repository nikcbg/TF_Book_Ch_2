# Webservers cluster with load balancer example 

### This folder contains Terraform code that deploys webservers cluster(using EC2 and Auto Scaling) and load balancer in AWS. The load balancer listens on port 80 and returns "Hello World text.
------------------------------------------------------------------------------------------------
### List of files in the repository:
- __main.tf__ - terraform configuration file and bash script.
- __variables.tf__ - terraform configuration file with input variables.
- __output.tf__ - terraform configuration file with output parameters.

- the code is broken down into 3 files for better description what each file does. 
- terraform will load all files in the directory ending in `.tf`.
---------------------------------------------------------------------------------------------------------------
###  Infrastructure resources to be created:
- __webservers cluster__ - group of servers (in this case EC2 instances) that are connected with each other.
   - __auto scaling group__ - automatically scale up or down group of resources (in this case EC2 instances).
- __load balancer__ - distributes workload across the webservers cluster.
-----------------------------------------------------------------------------------------------------------------
### Resources explanation of terraform code:
   ##### webserver cluster creation:
      - aws_launch_configuration - how to configure each EC2 instace(server) in auto scaling group(webservers cluster). 
      - aws_autoscaling_group - how many EC2 instances will be running referencing the aws_launch_configuration .









---------------------------------------------------------------------------------------------------------------
### How to use this repository:
- install `terraform` from [here](https://www.terraform.io/downloads.html).
- setup Amazon Web Services (AWS) account [here](https://aws.amazon.com/).
- configure your AWS access keys [here](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).
- configure your AWS access keys as environment variables so you can authenticate to your AWS account:

```
export AWS_ACCESS_KEY_ID="your access key id here"
export AWS_SECRET_ACCESS_KEY="your secret access key here"
```
   
- clone the repository to your local computer: `git clone https://github.com/nikcbg/TF_Book_Ch_2`.
- go into the cloned repo on your computer: `cd TF_Book_Ch_2`.
- go into the `cd one_webserver_with_variables` subfolder which is this example.

------------------------------------------------------------------------------------------------------------------
### Commands needed to build the webserver on the EC2 instance.
- execute `terraform init` - to initialize the provider and download the neccesery plugins.
  
- execute `terraform plan` - to create execution plan for changes to be applied, the output should diplay the following:  
```
Terraform will perform the following actions:

+ aws_autoscaling_group.example
+ aws_elb.example
+ aws_launch_configuration.example
+ aws_security_group.elb
+ aws_security_group.instance

Plan: 5 to add, 0 to change, 0 to destroy.
```
  
- execute `terraform apply` - to apply the desired changes, the output should diplay the following:

```
aws_security_group.instance: Creation complete after 6s (ID: sg-06a3b805b1b97cd3a)
aws_security_group.elb: Creation complete after 6s (ID: sg-0215914a82b675304)
aws_launch_configuration.example: Creation complete after 2s (ID: terraform-20190212120159356200000001)
aws_elb.example: Creation complete after 12s (ID: terraform-asg-example)
aws_autoscaling_group.example: Creation complete after 50s (ID: tf-asg-20190212120211504500000002)

Apply complete! Resources: 5 added, 0 changed, 0 destroyed.

Outputs:

elb_dns_name = terraform-asg-example-123456789.us-east-1.elb.amazonaws.com

```
  
- if you execute `curl http://terraform-asg-example-123456789.us-east-1.elb.amazonaws.com` in your terminal you should see `Hello, World` which means that everything works as expected.
  
- execute `terraform destroy` - to destroy the resource that we just created, the output should diplay the following:

```
aws_autoscaling_group.example: Destruction complete after 2m21s
aws_launch_configuration.example: Destruction complete after 1s
aws_security_group.instance: Destruction complete after 2s
aws_elb.example: Destruction complete after 3s
aws_security_group.elb: Destruction complete after 1m6s

Destroy complete! Resources: 5 destroyed.
```

