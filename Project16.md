# AUTOMATE INFRASTRUCTURE WITH IAC USING TERRAFORM PART 1


## Setup Workspace

- Create S3 bucket

![S3 Bucket](PBL-16/S3.png)

- Install and configure AWS CLI

```bash
# On Ubuntu

sudo apt install awscli

```

- Install Python SDK (boto3)

```bash

pip install boto3

```

- Access the bucket using AWS CLI

![awsS3](PBL-16/clitest.png)

- Access the bucket using boto3

![boto3S3](PBL-16/boto3.png)



## Create VPC and Subnets

- Create a directory and a file named main.tf in the directory
- Write the Provider and resources section

```HCL
provider "aws" {
	region = "us-east-2"
}

resource "aws_vpc" "main" {
	cidr_block						= "172.16.0.0/16"
	enable_dns_support				= "true"
	enable_dns_hostname				= "true"
	enable_classiclink				= "false"
	enable_classiclink_dns_support	= "false"
}
```


- Run ```terraform init```

![terraform init](PBL-16/tinit.png)

- Run ```terraform plan```

![terraform plan](PBL-16/fplan.png)

- Run ```terraform apply```

![terraform apply](PBL-16/fapply1.png)
![terraform apply](PBL-16/fapply2.png)
![viewVPC](PBL-16/vpc.png)
![viewSUBNETS](PBL-16/subnets.png)

- Run ```terraform destroy```

![terraformdestroy](PBL-16/tdestroy1.png)
![vpc](PBL-16/bvpc.png)
![subnets](PBL-16/bsubnets.png)


## Refacor the Code

To refactor the code you have to 
- Fix Hard coded values
- Fix multiple resource blocks
- Make the cidr_block dynamic
- Introduce ```variables.tf``` and ```terraform.tfvars```

__The final code repo is available [here](https://github.com/Horleryheancarh/PBL-IaC)__

