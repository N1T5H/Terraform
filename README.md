# Terraform AWS Remote State Backend

This project provides a Terraform configuration for setting up a robust remote state backend using AWS S3 and DynamoDB. It's designed to help you manage your Terraform state files securely and efficiently in a cloud environment.

## Features

- **S3 Bucket**: Configures an S3 bucket for storing Terraform state files.
- **DynamoDB Table**: Sets up a DynamoDB table for state locking, preventing concurrent modifications.
- **Encryption**: Ensures state files are encrypted at rest in the S3 bucket.
- **Environment-Specific Configurations**: Supports multiple environments (e.g., dev, staging, prod) through variable files.

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/n1t5h/terraform-aws-remote-state-backend.git
   cd terraform-aws-remote-state-backend
   ```

2. Create a `config/backend-<env>.conf` file for your environment-specific backend configuration.

3. Create a `config/<env>.tfvars` file for your environment-specific variables.

4. Initialize and apply the Terraform configuration:
   ```bash
   env=dev
   terraform get -update=true
   terraform init -backend-config=config/backend-${env}.conf
   terraform plan -var-file=config/${env}.tfvars
   terraform apply -var-file=config/${env}.tfvars
   ```

## Configuration

The `main.tf` file contains the core configuration for the S3 backend:

```terraform
terraform {
  backend "s3" {
    encrypt = true
    bucket  = "-terraform-states"
    key     = "development/service-name.tfstate"
    region  = "ap-southeast-2"
    dynamodb_table = "terraform-lock"
  }
}
```

Adjust the `bucket`, `key`, `region`, and `dynamodb_table` values as needed for your specific setup.

