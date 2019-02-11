# Single server example 

### This folder contains Terraform example code that deploys a single virtual server(EC2 instance) in AWS.
------------------------------------------------------------------------------------------------

### List of parameters in the Terraform code:
- __*provider*__ - platform that is used to create resources, in this example AWS.
- __*region*__ - AWS region is a datacenter located in certain geographic area.
- __*resource*__ - servers(EC2), databases(RDS), load balancers, etc. 
- __*ami*__ - Amazon Machine Image provides the information required to launch a virtual server(EC2) in the AWS.
- __*instance_type*__ - type of virtual server(EC2) with certain amount of CPU, memory, disk space and network capacity. 
- __*tags*__ - label that is applied to resource, such as name of the resource that's been doployed. 
------------------------------------------------------------------------------------------------------------------

### How to use this repository:
- install `terraform` from [here](https://www.terraform.io/downloads.html)
- setup Amazon Web Services (AWS) account [here](https://aws.amazon.com/)
- configure your AWS access keys [here](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)
- configure your AWS access keys as environment variables:

```
export AWS_ACCESS_KEY_ID="your access key id here"
export AWS_SECRET_ACCESS_KEY="your secret access key here"
```
   
- clone the repository to your local computer: `git clone https://github.com/nikcbg/TF_Book_Ch_2`.
- go into the cloned repo on your computer: `cd TF_Book_Ch_2`.
- go into the `cd one_server` subfolder which is this example.
 
### Commands needed to build the EC2 instance.
- execute `terraform init` - to initialize the provider and download the neccesery plugins.
  
- execute `terraform plan` - to create execution plan for changes to be applied, the output should diplay the following:  

```
Terraform will perform the following actions:

  + aws_instance.example
      ami:                          "ami-40d28157"
      availability_zone:            <computed>
      instance_type:                "t2.micro"
      private_dns:                  <computed>
      private_ip:                   <computed>
      public_dns:                   <computed>
      public_ip:                    <computed>
      security_groups.#:            <computed>
      subnet_id:                    <computed>
      tags.%:                       "1"
      tags.Name:                    "terraform-example"
      vpc_security_group_ids.#:     <computed>

 Plan: 1 to add, 0 to change, 0 to destroy.

```
  
- execute `terraform apply` - to apply the desired changes, the output should diplay the following:

```
aws_instance.example: Still creating... (10s elapsed)
aws_instance.example: Still creating... (20s elapsed)
aws_instance.example: Still creating... (30s elapsed)
aws_instance.example: Creation complete after 38s (ID: i-0a13861fd52f8d2c1)

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
```
  
- execute `terraform destroy` - to destroy the resource that we just created, the output should diplay the following:

```
aws_instance.example: Destroying... (ID: i-0a13861fd52f8d2c1)
aws_instance.example: Still destroying... (ID: i-0a13861fd52f8d2c1, 10s elapsed)
aws_instance.example: Still destroying... (ID: i-0a13861fd52f8d2c1, 20s elapsed)
aws_instance.example: Still destroying... (ID: i-0a13861fd52f8d2c1, 30s elapsed)
aws_instance.example: Still destroying... (ID: i-0a13861fd52f8d2c1, 40s elapsed)
aws_instance.example: Still destroying... (ID: i-0a13861fd52f8d2c1, 50s elapsed)
aws_instance.example: Still destroying... (ID: i-0a13861fd52f8d2c1, 1m0s elapsed)
aws_instance.example: Still destroying... (ID: i-0a13861fd52f8d2c1, 1m10s elapsed)
aws_instance.example: Destruction complete after 1m16s

Destroy complete! Resources: 1 destroyed.  
```

