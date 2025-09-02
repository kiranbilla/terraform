Absolutely! Here’s a **quick setup guide** plus **handy tricks** for Terraform across AWS, GCP, and Azure, so you can spin up infrastructure faster and smarter.

---

# Terraform Quick Setup & Tricks

---

## Quick Setup Steps (Common for all Clouds)

### 1. Install Terraform

* Download the latest version from [terraform.io](https://www.terraform.io/downloads.html)
* Add Terraform to your system PATH
* Verify install:

```bash
terraform -version
```

### 2. Set Up CLI Credentials for Each Cloud

**AWS:**

```bash
aws configure
# or export env vars:
export AWS_ACCESS_KEY_ID=xxxx
export AWS_SECRET_ACCESS_KEY=xxxx
export AWS_REGION=us-east-1
```

**GCP:**

* Create a service account JSON key
* Authenticate:

```bash
gcloud auth activate-service-account --key-file=key.json
export GOOGLE_APPLICATION_CREDENTIALS="path/to/key.json"
```

**Azure:**

```bash
az login
# or use service principal:
az ad sp create-for-rbac --name "terraform-sp" --role Contributor --scopes /subscriptions/xxxx
export ARM_CLIENT_ID=xxxx
export ARM_CLIENT_SECRET=xxxx
export ARM_SUBSCRIPTION_ID=xxxx
export ARM_TENANT_ID=xxxx
```

### 3. Write a Minimal Terraform Config (Example: AWS S3 Bucket)

`main.tf`:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "mybucket" {
  bucket = "my-unique-bucket-name-12345"
  acl    = "private"
}
```

### 4. Initialize & Apply

```bash
terraform init
terraform plan
terraform apply
```

---

## Handy Terraform Tricks

### 1. Use Variables for Reusability

```hcl
variable "region" {
  default = "us-east-1"
}
provider "aws" {
  region = var.region
}
```

Pass vars on CLI:

```bash
terraform apply -var="region=us-west-2"
```

### 2. Use `terraform fmt` to Auto Format Code

Keeps your HCL files clean and readable.

```bash
terraform fmt
```

### 3. Use Remote State Backends Early

Avoid state conflicts by using remote backends like S3/GCS/Azure Blob:

```hcl
terraform {
  backend "s3" {
    bucket = "my-terraform-state-bucket"
    key    = "state/terraform.tfstate"
    region = "us-east-1"
  }
}
```

### 4. Use Workspaces for Environment Segregation

```bash
terraform workspace new dev
terraform workspace select dev
terraform apply
```

### 5. Use Data Sources to Reference Existing Resources

```hcl
data "aws_ami" "ubuntu" {
  most_recent = true
  owners      = ["099720109477"]
  filter {
    name   = "name"
    values = ["ubuntu/images/hvm-ssd/ubuntu-focal-20.04-amd64-server-*"]
  }
}
resource "aws_instance" "web" {
  ami           = data.aws_ami.ubuntu.id
  instance_type = "t2.micro"
}
```

### 6. Manage Secrets Securely

* Don’t hardcode secrets. Use environment variables or tools like Vault.
* Example for AWS credentials:

```bash
export AWS_ACCESS_KEY_ID=xxx
export AWS_SECRET_ACCESS_KEY=xxx
```

### 7. Automate with CI/CD

Integrate Terraform plan/apply in pipelines (GitHub Actions, Jenkins). Use environment variables for credentials and terraform workspaces for environments.

### 8. Use Modules for Reusable Code

Example to call a module:

```hcl
module "vpc" {
  source = "terraform-aws-modules/vpc/aws"
  version = "3.0.0"
  name = "my-vpc"
  cidr = "10.0.0.0/16"
}
```

---

## Bonus: Multi-Cloud Provider Setup in One Config

```hcl
provider "aws" {
  region = "us-east-1"
  alias  = "aws"
}

provider "google" {
  project = "my-gcp-project"
  region  = "us-central1"
  alias   = "gcp"
}

resource "aws_s3_bucket" "bucket" {
  provider = aws.aws
  bucket   = "my-aws-bucket"
}

resource "google_storage_bucket" "bucket" {
  provider = google.gcp
  name     = "my-gcp-bucket"
  location = "US"
}
```

Run everything with one `terraform apply`.


