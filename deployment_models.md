Deploying multiple Terraform scripts (or configurations) that manage different sets of resources at the same time can be achieved in several ways. Here are some effective methods to accomplish this:
### Method 1: Combining Configurations into a Single Configuration

If the resources are logically related, the best practice is to combine them into a single Terraform configuration. This way, you can manage dependencies and apply the changes in a coordinated manner.
Example Directory Structure

css

project/
├── main.tf
├── vpc.tf
├── ec2.tf
└── outputs.tf

Example main.tf

hcl

provider "aws" {
  region = "us-east-1"
}

module "vpc" {
  source = "./vpc"
}

module "ec2" {
  source = "./ec2"
}

### Method 2: Using Terraform Modules

Encapsulate different resources into modules and call these modules from a single root module. This approach allows you to keep the configurations modular and reusable.
Example Module Usage

main.tf

hcl

provider "aws" {
  region = "us-east-1"
}

module "vpc" {
  source = "./modules/vpc"
}

module "ec2" {
  source = "./modules/ec2"
}

module "s3" {
  source = "./modules/s3"
}

### Method 3: Using a Wrapper Script to Apply Multiple Configurations

If the configurations are independent but need to be applied at the same time, you can use a wrapper script to orchestrate the execution of terraform apply for each configuration directory.
Example Shell Script

sh

#!/bin/bash

#List of directories containing Terraform configurations
configs=("path/to/config1" "path/to/config2" "path/to/config3")

for config in "${configs[@]}"
do
    echo "Deploying configuration in $config"
    cd $config

    # Initialize and apply the configuration
    terraform init
    terraform apply -auto-approve

    cd -
done

 ### Method 4: Using Terraform Workspaces

If the resources need to be managed in separate environments but share similar configurations, you can use Terraform workspaces.
Example Workspace Usage

# sh

terraform workspace new dev
terraform apply

terraform workspace new staging
terraform apply

terraform workspace new prod
terraform apply

### Method 5: Using CI/CD Pipelines

# Integrate Terraform with a CI/CD tool like Jenkins, GitHub Actions, GitLab CI, etc., to automate the deployment process. You can set up jobs to deploy multiple configurations concurrently or in sequence.
Example GitHub Actions Workflow

yaml

name: Deploy Multiple Terraform Configurations

on:
  push:
    branches:
      - main

jobs:
  terraform:
    name: Terraform Deploy
    runs-on: ubuntu-latest
    strategy:
      matrix:
        config-path: 
          - path/to/config1
          - path/to/config2
          - path/to/config3

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Set up Terraform
        uses: hashicorp/setup-terraform@v1

      - name: Initialize Terraform
        run: terraform init
        working-directory: ${{ matrix.config-path }}

      - name: Apply Terraform configuration
        run: terraform apply -auto-approve
        working-directory: ${{ matrix.config-path }}

## Best Practices

  #  State Management: Ensure that each configuration uses a separate state file to avoid conflicts.
  #  Dependencies: Manage dependencies between resources carefully to ensure correct provisioning order.
  #  Error Handling: Implement error handling in scripts to manage failures gracefully.
  #  Documentation: Document the structure and purpose of each configuration for maintainability.

