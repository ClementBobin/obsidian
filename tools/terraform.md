# Terraform Cheat-Sheet

Terraform is a free and open-source infrastructure as code automation tool, used for provisioning, changing, and versioning resources across any environment.

- **Project Homepage**: [Terraform by HashiCorp](https://www.terraform.io/)
    
- **Documentation**: [Documentation | Terraform by HashiCorp](https://www.terraform.io/docs)
    
- **TF Registry**: [Terraform Registry](https://registry.terraform.io/)
    

---

## 🔍 Overview

- **Product Type**: Infrastructure as Code (IaC) Tool
    
- **Focus**: Automating and managing infrastructure deployments across different cloud providers and environments.
    
- **Use Cases**: Managing virtual machines, networks, storage, and other infrastructure resources.
    

---

## 🔧 Format and Validate

|COMMAND|DESCRIPTION|
|---|---|
|`terraform fmt`|Reformat your configuration in the standard style|
|`terraform validate`|Check whether the configuration is valid|

---

## ⚙️ Initialize Working Directory

|COMMAND|DESCRIPTION|
|---|---|
|`terraform init`|Prepare your working directory for other commands|

---

## 🚀 Plan, Deploy, and Cleanup

|COMMAND|DESCRIPTION|
|---|---|
|`terraform apply --auto-approve`|Create or update infrastructure without a confirmation prompt|
|`terraform destroy --auto-approve`|Destroy previously-created infrastructure without confirmation prompt|
|`terraform plan -out plan.out`|Output the deployment plan to `plan.out`|
|`terraform apply plan.out`|Use `plan.out` to deploy infrastructure|
|`terraform plan -destroy`|Outputs a destroy plan|
|`terraform apply -target=aws_instance.myinstance`|Only apply/deploy changes to targeted resource|
|`terraform apply -var myregion=us-east-1`|Pass a variable via CLI while applying a configuration|
|`terraform apply -lock=true`|Lock the state file so it can't be modified|
|`terraform apply refresh=false`|Do not reconcile state file with real-world resources|
|`terraform apply --parallelism=5`|Number of simultaneous resource operations|
|`terraform refresh`|Reconcile the state in Terraform state file with real-world resources|
|`terraform providers`|Get information about providers used in the current configuration|

---

## 🧑‍💻 Workspaces

|COMMAND|DESCRIPTION|
|---|---|
|`terraform workspace new myworkspace`|Create a new workspace|
|`terraform workspace select default`|Change to a workspace|
|`terraform workspace list`|List all workspaces|

---

## 📂 State Manipulation

|COMMAND|DESCRIPTION|
|---|---|
|`terraform state show aws_instance.myinstance`|Show details stored in the Terraform state file|
|`terraform state pull > terraform.tfstate`|Output Terraform state to a file|
|`terraform state mv aws_iam_role.my_ssm_role module.mymodule`|Move a resource tracked via state to a different module|
|`terraform state replace-provider hashicorp/aws registry.custom.com/aws`|Replace an existing provider with another|
|`terraform state list`|List all resources tracked in the Terraform state file|
|`terraform state rm aws_instance.myinstance`|Unmanage a resource, delete it from the Terraform state file|

---

## 📥 Import and Outputs

|COMMAND|DESCRIPTION|
|---|---|
|`terraform import resourcetype.myresource <id>`|Import a resource|
|`terraform output`|List all outputs|
|`terraform output <output>`|List a specific output|
|`terraform output -json`|List all outputs in JSON format|

---

## 🌩️ Terraform Cloud

|COMMAND|DESCRIPTION|
|---|---|
|`terraform login`|Login to Terraform Cloud with an API token|
|`terraform logout`|Logout from Terraform Cloud|

---

## 🛠️ Import Existing Resources

You can use `terraform import` to bring existing infrastructure into Terraform management. The basic syntax for importing a resource is:

```bash
terraform import <RESOURCE_TYPE>.<NAME> <ID>
```

For example:

```bash
terraform import aws_instance.my_instance i-1234567890abcdef0
```

This command will allow Terraform to start managing the resource identified by the provided `<ID>`.

---

## 🔁 Related

- **Infrastructure as Code (IaC)**
    
- **Automation Tools**
    
- **[AWS CloudFormation](https://aws.amazon.com/cloudformation/)**: Alternative IaC tool for AWS.
    
- **Kubernetes**: IaC for containerized workloads.
    

---

## 🔍 Explore More

- **Terraform Basics**: Learn the fundamentals of using Terraform.
    
- **Terraform Providers**: Detailed documentation on using providers with Terraform.
    
- **Terraform Modules**: A deeper dive into using modules in your Terraform configurations.
    
- **Terraform State Management**: Learn how Terraform manages state files and how to manipulate them.
    
- **Terraform Cloud**: Explore Terraform's cloud-based infrastructure management tools.
    

---

## 🏷️ Tags

#terraform  
#infrastructure-as-code  
#automation  
#cloud-architecture  
#devops  
#state-management  
#terraform-cloud