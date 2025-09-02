# Terraform 30-Day Roadmap: Zero to Hero  
*Basic to Advanced | AWS | GCP | Azure | Multi-Cloud Setup | Repo Best Practices*

---

## Overview

This roadmap is designed to take you from a Terraform beginner to an advanced user capable of deploying and managing infrastructure across multiple clouds (AWS, GCP, Azure). Each day includes concepts to learn, hands-on exercises, and important notes to master Terraform and multi-cloud infra as code.

---

## Day 1: Introduction to Terraform & IaC
- **Concepts:** What is Terraform? Benefits of IaC.
- **Tasks:** Install Terraform. Run `terraform --version`.
- **Notes:** Understand declarative vs imperative infra.

## Day 2: Terraform Basics - Configuration Files
- **Concepts:** Terraform configuration files, HCL syntax.
- **Tasks:** Write a simple `main.tf` to create a local file resource.
- **Notes:** Understand providers and resources.

## Day 3: Terraform CLI & Workflow
- **Concepts:** `terraform init`, `plan`, `apply`, `destroy`.
- **Tasks:** Run basic Terraform workflow with your config.
- **Notes:** Importance of state files.

## Day 4: Variables & Outputs
- **Concepts:** Input variables, default values, outputs.
- **Tasks:** Parameterize your config with variables; add outputs.
- **Notes:** Use `terraform.tfvars` for environment variables.

## Day 5: State Management Basics
- **Concepts:** What is state? Local vs remote state.
- **Tasks:** Inspect state file; try `terraform show`.
- **Notes:** Avoid manual edits to state.

## Day 6: Providers Deep Dive: AWS Setup
- **Concepts:** AWS provider configuration.
- **Tasks:** Create an S3 bucket with Terraform on AWS.
- **Notes:** Use IAM roles and policies securely.

## Day 7: AWS Resources - Compute
- **Concepts:** EC2 instances, security groups basics.
- **Tasks:** Launch an EC2 instance with a security group.
- **Notes:** Understand AWS resource dependencies.

## Day 8: AWS Resources - Networking
- **Concepts:** VPC, subnets, route tables.
- **Tasks:** Create a VPC with public and private subnets.
- **Notes:** CIDR block planning.

## Day 9: AWS Advanced - Load Balancers & Autoscaling
- **Concepts:** ALB, Target Groups, Auto Scaling Groups.
- **Tasks:** Create an ALB and attach EC2 instances.
- **Notes:** Use Terraform modules for reusability.

## Day 10: Introduction to Terraform Modules
- **Concepts:** What are modules? Creating reusable code.
- **Tasks:** Create a simple module for EC2.
- **Notes:** Use public modules from the Terraform Registry.

---

## Day 11: GCP Provider Setup
- **Concepts:** GCP provider authentication & setup.
- **Tasks:** Create a GCP project & a simple VM instance.
- **Notes:** Use service accounts for auth.

## Day 12: GCP Networking Basics
- **Concepts:** VPC networks, firewall rules.
- **Tasks:** Create a VPC and firewall rule.
- **Notes:** Understand default networks vs custom.

## Day 13: GCP Compute Resources
- **Concepts:** Compute Engine instances.
- **Tasks:** Deploy a VM with startup script.
- **Notes:** Use metadata for configuration.

## Day 14: Azure Provider Setup
- **Concepts:** Azure provider configuration.
- **Tasks:** Create a Resource Group & Virtual Machine.
- **Notes:** Understand Azure Resource Manager (ARM).

## Day 15: Azure Networking
- **Concepts:** Virtual Networks, Network Security Groups.
- **Tasks:** Deploy a VNet and NSG.
- **Notes:** Use Azure CLI for authentication.

---

## Day 16: Azure Storage & Database Resources
- **Concepts:** Storage Accounts, Azure SQL.
- **Tasks:** Create a storage account and SQL DB.
- **Notes:** Secure credentials with Key Vault.

## Day 17: Terraform State Remote Backends
- **Concepts:** Remote state with S3, GCS, Azure Blob.
- **Tasks:** Configure remote backend for AWS S3.
- **Notes:** Locking and state consistency.

## Day 18: Terraform Workspaces for Environment Management
- **Concepts:** Workspaces for dev/prod isolation.
- **Tasks:** Create and switch workspaces.
- **Notes:** Workspace naming conventions.

## Day 19: Terraform Data Sources
- **Concepts:** Reading external data into Terraform.
- **Tasks:** Use AWS AMI data source.
- **Notes:** Data sources do not create resources.

## Day 20: Terraform Expressions & Functions
- **Concepts:** Built-in functions, conditionals, loops.
- **Tasks:** Use `count`, `for_each`, and `lookup`.
- **Notes:** Dynamic resource creation.

---

## Day 21: Advanced Terraform Modules
- **Concepts:** Module inputs, outputs, versioning.
- **Tasks:** Refactor infra using nested modules.
- **Notes:** Module version pinning best practice.

## Day 22: Multi-Cloud Setup - Strategy & Architecture
- **Concepts:** Multi-cloud benefits and challenges.
- **Tasks:** Plan multi-cloud infra design.
- **Notes:** Avoid vendor lock-in with abstraction.

## Day 23: Multi-Cloud Deployment: AWS + GCP
- **Concepts:** Using multiple providers in one config.
- **Tasks:** Deploy infra in AWS & GCP simultaneously.
- **Notes:** Provider aliases and workspace use.

## Day 24: Multi-Cloud Deployment: Azure + AWS
- **Concepts:** Cross-cloud networking basics.
- **Tasks:** Deploy a VM in Azure and DB in AWS.
- **Notes:** Secure API keys for each provider.

## Day 25: Terraform Best Practices: File Structure & Naming
- **Concepts:** Organizing files, naming conventions.
- **Tasks:** Reorganize configs into logical folders.
- **Notes:** Use `.tfvars` files and `.gitignore`.

---

## Day 26: Repo Setup for Terraform Projects
- **Concepts:** Git workflows, branching strategies.
- **Tasks:** Initialize git repo; commit best practices.
- **Notes:** Avoid committing sensitive data.

## Day 27: CI/CD Pipelines for Terraform
- **Concepts:** Integrate Terraform in Jenkins/GitHub Actions.
- **Tasks:** Create simple pipeline to run `plan` & `apply`.
- **Notes:** Use environment variables for secrets.

## Day 28: Terraform Security & Secrets Management
- **Concepts:** Managing secrets in Terraform.
- **Tasks:** Use HashiCorp Vault or cloud KMS.
- **Notes:** Never hardcode secrets.

## Day 29: Troubleshooting & Debugging Terraform
- **Concepts:** Debug logs, common errors.
- **Tasks:** Simulate and fix errors.
- **Notes:** Use `terraform validate` and `fmt`.

## Day 30: Wrap-Up Project: Multi-Cloud Infra as Code
- **Concepts:** Build a complete infra using AWS, GCP, Azure.
- **Tasks:** Use modules, remote state, workspaces, secrets.
- **Notes:** Document your repo README with architecture.

---

# Resources & References
- [Terraform Docs](https://www.terraform.io/docs)
- [AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [GCP Provider](https://registry.terraform.io/providers/hashicorp/google/latest/docs)
- [Azure Provider](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)
- [Terraform Registry Modules](https://registry.terraform.io/)

---

*Happy Terraforming! 🚀*

