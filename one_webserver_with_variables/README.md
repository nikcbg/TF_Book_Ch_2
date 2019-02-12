# Single webserver example 

### This folder contains Terraform example code that deploys a webserver on the EC2 instance I created in one_server example in AWS. The webserver listens on port 8080 and returns "Hello World text.
------------------------------------------------------------------------------------------------
### List of files in the repository:
- main.tf - file with terraform confoguration code and bash script.

---------------------------------------------------------------------------------------------------------------
### Allowing traffic on the EC2 instance so the webserver is accessible:
- creating `aws_security_group` resource in `main.tf` file code to allow incoming traffic:

```
resource "aws_security_group" "instance" {
  name = "terraform-example-instance"

  ingress {
    from_port   = 8080
    to_port     = 8080
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```
- next you need to tell the EC2 instance to use the security group you just created:

```
resource "aws_instance" "example" {
  ami                    = "ami-40d28157"
  instance_type          = "t2.micro"
  vpc_security_group_ids = ["${aws_security_group.instance.id}"]
```

------------------------------------------------------------------------------------------------------------------

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
- go into the `cd one_webserver` subfolder which is this example.

------------------------------------------------------------------------------------------------------------------
### Commands needed to build the webserver on the EC2 instance.
- execute `terraform init` - to initialize the provider and download the neccesery plugins.
  
- execute `terraform plan` - to create execution plan for changes to be applied, the output should diplay the following:  

```

```
  
- execute `terraform apply` - to apply the desired changes, the output should diplay the following:

```


```
  
  
- execute `terraform destroy` - to destroy the resource that we just created, the output should diplay the following:

```

```

