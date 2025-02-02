# Terraform AWS Remote State Backend

This project provides a Terraform configuration for setting up a robust remote state backend using AWS S3 and DynamoDB. It's designed to help you manage your Terraform state files securely and efficiently in a cloud environment.

## Features

- **S3 Bucket**: Configures an S3 bucket for storing Terraform state files.
- **DynamoDB Table**: Sets up a DynamoDB table for state locking, preventing concurrent modifications.
- **Encryption**: Ensures state files are encrypted at rest in the S3 bucket.
- **Environment-Specific Configurations**: Supports multiple environments (e.g., dev, staging, prod) through variable files.

Usage Instructions
Make sure you're using the correct AWS account:
bash
pip install awscli
aws s3 ls
If you haven't set a default region in your AWS configuration and want to create resources in "us-east-1":
bash
export AWS_DEFAULT_REGION=us-east-1
export AWS_REGION=us-east-1
Initialize Terraform:
bash
terraform init
Plan the changes:
bash
terraform plan -var="account_id=<your-aws-account-id>"
Apply the changes:
bash
terraform apply -var="account_id=<your-aws-account-id>"
After applying, Terraform will create an S3 bucket named <account_id>-terraform-states and a DynamoDB table named terraform-lock. These can be used as a backend for other Terraform configurations

