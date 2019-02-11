## Single server example 

### This folder contains Terraform example code that deploys a single server(EC2 instance) in AWS.
------------------------------------------------------------------------------------------------

### List of parameters in the Terraform code:
- __*provider*__ - platform that is used to create resources, in this example AWS.
- __*region*__ - AWS region is a datacenter located in certain geographic area.
- __*resource*__ - servers (EC2), databases(RDS), load balancers, etc. 
- __*ami*__ - Amazon Machine Image provides the information required to launch a virtual server(EC2) in the AWS.
- __*instance_type*__ - type of virtual server(EC2) with certain amount of CPU, memory, disk space and network capacity. 
- __*tags*__ - label that is applied to resource, such as name of the resource that's been doployed. 
------------------------------------------------------------------------------------------------------------------





### To be able to execute the code you will need to meet the following pre-requisites:
- you need to install `terraform` from [here](https://www.terraform.io/downloads.html)
- you need to setup Amazon Web Services (AWS) account [here](https://aws.amazon.com/)
- you need to configure your AWS access keys [here](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)
- you need to configure your AWS access keys as environment variables:
   ```
    export AWS_ACCESS_KEY_ID="your access key id here"
    export AWS_SECRET_ACCESS_KEY="your secret access key here"
   ```
