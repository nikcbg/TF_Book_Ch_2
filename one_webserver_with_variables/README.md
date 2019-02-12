# Single webserver example 

### This folder contains Terraform example code with input variables that deploys a webserver on the EC2 instance in AWS. The webserver listens on port 8080 and returns "Hello World text.
------------------------------------------------------------------------------------------------
### List of files in the repository:
- main.tf - terraform confoguration file and bash script.
- variables.tf - terraform configuration file with input variables.
- output.tf - terraform configuration file with output parameters.

- the code is broken down into 3 files for better description what each file does. 
- terraform will load all files in the directory ending in `.tf`.
---------------------------------------------------------------------------------------------------------------
### Input variables parameters(all 3 parameters are optional) and benefits:
- __*description*__ - to document how a variable is used.
- __*default*__ - to provide a value of the variable.
- __*type*__ - must be one of "string", "list" or "map"

- with variables your terraform code is more configurable, efficient, flexible and reusable.
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
+ aws_security_group.instance
     
      description:                          "Managed by Terraform"
      egress.#:                             <computed>
      ingress.#:                            "1"
      ingress.516175195.cidr_blocks.#:      "1"
      ingress.516175195.cidr_blocks.0:      "0.0.0.0/0"
      ingress.516175195.from_port:          "8080"
      ingress.516175195.protocol:           "tcp"
      ingress.516175195.security_groups.#:  "0"
      ingress.516175195.self:               "false"
      ingress.516175195.to_port:            "8080"
      name:                                 "terraform-example-instance


Plan: 2 to add, 0 to change, 0 to destroy.

```
  
- execute `terraform apply` - to apply the desired changes, the output should diplay the following:

```
aws_instance.example: Still creating... (10s elapsed)
aws_instance.example: Still creating... (20s elapsed)
aws_instance.example: Still creating... (30s elapsed)
aws_instance.example: Creation complete after 34s (ID: i-0e4f764968ed93051)

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.

Outputs:

public_ip = 123.456.789.111

```
  
- if you execute `curl http://EC2_public_IP_address:8080` in your terminal you should see `Hello, World` which means that everything works as expected.
  
- execute `terraform destroy` - to destroy the resource that we just created, the output should diplay the following:

```
aws_instance.example: Destruction complete after 1m8s
aws_security_group.instance: Destroying... (ID: sg-00cd9bd2ea8e356cb)
aws_security_group.instance: Destruction complete after 2s

Destroy complete! Resources: 2 destroyed.

```

