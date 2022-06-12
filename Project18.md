# AUTOMATE INFRASTRUCTURE WITH IaC USING TERRAFORM PART 3

### Introducing Backend On S3

- Create a file and name it ```backend.tf```

```tf
resource "aws_s3_bucket" "terraform_state" {
  bucket = "yheancarh-dev-terraform-bucket"
}

resource "aws_s3_bucket_versioning" "terraform_state" {
  bucket = aws_s3_bucket.terraform_state.id

  versioning_configuration {
    status = "Enabled"
  }
}

resource "aws_s3_bucket_server_side_encryption_configuration" "terraform_state" {
  bucket = aws_s3_bucket.terraform_state.bucket
  rule {
    apply_server_side_encryption_by_default {
      sse_algorithm = "AES256"
    }
  }
}
```

- Create a DynamoDB table for the lock file and consistency checks

```tf
resource "aws_dynamodb_table" "terraform_locks" {
  name         = "terraform-locks"
  billing_mode = "PAY_PER_REQUEST"
  hash_key     = "LockID"
  attribute {
    name = "LockID"
    type = "S"
  }
}
```

- Configure the S3 backend

```tf
terraform {
  backend "s3" {
    bucket         = "yheancarh-dev-terraform-bucket"
    key            = "global/s3/terraform.tfstate"
    region         = "us-east-2"
    dynamodb_table = "terraform-locks"
    encrypt        = true
  }
}
```

- Verify the changes

![S3](PBL-18/s3.png)

![dynamo](PBL-18/db.png)


### Rafactoring Terraform Using Modules

- Setup the modules directory

![tree](PBL-18/tree.png)

- Run ```terraform init``` to initialize the modules

- Run ```terraform fmt``` to format the files

![fmt](PBL-18/fmt.png)

- Run ```terraform plan``` 

![plan](PBL-18/plan.png)

- Run ```terraform apply``` and ```terraform destroy``` to test the configurations

![test](PBL-18/test.png)