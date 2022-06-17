# AUTOMATE INFRASTRUCTURE WITH IaC USING TERRAFORM PART 4


### Migrate codes to Terraform Cloud

- Create a Terraform Cloud Account
- Create an organization
- Configure a Workspace ----
- Configure variables
- Build AMIs with packer

```bash
packer build bastion.pkr.hcl

packer build web.pkr.hcl

packer build nginx.pkr.hcl

packer build ubuntu.pkr.hcl
```

![Packer](PBL-19/packer1.png)

- AMIs

![AMIs](PBL-19/ami.png)

- Run ```terraform plan``` and ```terraform apply``` from web console

![TestApply](PBL-19/test.png)

- Test automated ```terraform plan```

![AutoTest](PBL-19/autotest.png)


### Practice Task 1

<!-- - Configure 3 branches in terraform-cloud repository for _dev_, _test_ and _prod_ environments
- Make neccesary configurations to trigger runs automatically for the _dev_ environment -->
- Create an Email nofitications for certain events

![Mail](PBL-19/mail.png)

- Apply _destroy_ from Terraform Cloud web console

![Destroy](PBL-19/destroy.png)


<!-- ### Practice Task 2

- Create a simple Terraform repository that will be your module
- Import the module to your private registry
- Create a configuration that uses the module
- Create a workspace for the configuration 
- Deploy the infrastructure
- Destroy the deployment -->