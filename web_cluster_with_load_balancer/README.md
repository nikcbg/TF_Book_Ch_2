# Webservers cluster with load balancer example 

### This folder contains Terraform code that deploys webservers cluster(using EC2 and Auto Scaling) and load balancer in AWS. The load balancer listens on port 80 and returns "Hello World text.
------------------------------------------------------------------------------------------------
### List of files in the repository:
- main.tf - terraform confoguration file and bash script.
- variables.tf - terraform configuration file with input variables.
- output.tf - terraform configuration file with output parameters.

- the code is broken down into 3 files for better description what each file does. 
- terraform will load all files in the directory ending in `.tf`.
---------------------------------------------------------------------------------------------------------------
### Components of the infrastructure to be created:
- __webservers cluster__ - group of servers (in this case EC2 instances) that are connected with each other.
   - __auto scaling__ - automatically scale up or down groups of resources (in this case EC2 instances)
- __load balancer__ - distributes workload across the webservers cluster.
-----------------------------------------------------------------------------------------------------------------

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

```
  
- execute `terraform apply` - to apply the desired changes, the output should diplay the following:

```
aws_instance.example: Still creating... (10s elapsed)

```
  
- if you execute `curl http://EC2_public_IP_address:8080` in your terminal you should see `Hello, World` which means that everything works as expected.
  
- execute `terraform destroy` - to destroy the resource that we just created, the output should diplay the following:

```

```

