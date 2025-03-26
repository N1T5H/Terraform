# Terraform AWS Remote State Backend

This project provides a Terraform configuration for setting up a robust remote state backend using AWS S3 and DynamoDB. It's designed to help you manage your Terraform state files securely and efficiently in a cloud environment.

## Features

- **S3 Bucket**: Configures an S3 bucket for storing Terraform state files.
- **DynamoDB Table**: Sets up a DynamoDB table for state locking, preventing concurrent modifications.
- **Encryption**: Ensures state files are encrypted at rest in the S3 bucket.
- **Environment-Specific Configurations**: Supports multiple environments (e.g., dev, staging, prod) through variable files.


## Usage Instructions

1. Make sure you're using the correct AWS account:
   ```bash
   pip install awscli
   aws s3 ls
   ```

2. If you haven't set a default region in your AWS configuration and want to create resources in "us-east-1":
   ```bash
   export AWS_DEFAULT_REGION=us-east-1
   export AWS_REGION=us-east-1
   ```

3. Initialize Terraform:
   ```bash
   terraform init
   ```

4. Plan the changes:
   ```bash
   terraform plan
   ```

5. Apply the changes:
   ```bash
   terraform apply 
   ```



