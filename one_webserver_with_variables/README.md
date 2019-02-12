# Single webserver example 

### This folder contains Terraform example code with input variables that deploys a webserver on the EC2 instance in AWS. The webserver listens on port 8080 and returns "Hello World text.
------------------------------------------------------------------------------------------------
### List of files in the repository:
- main.tf - terraform confoguration file and bash script.
- variables.tf - terraform configuration file with input variables.
- output.tf - terraform configuration file with output parameters.

- terraform will load all files in the directory ending in `.tf`.
---------------------------------------------------------------------------------------------------------------
### Input variables parameters (all 3 parameters are optional):
- __*description*__ - to document how a variable is used.
- __*default*__ - to provide a value of the variable.
- __*type*__ - must be one of "string", "list" or "map"
-----------------------------------------------------------------------------------------------------------------
### Allowing traffic on the EC2 instance with variables so the webserver is accessible:


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
- go into the `cd one_webserver_with_variables` subfolder which is this example.

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

