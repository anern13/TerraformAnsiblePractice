# Terraform and Ansible Infrastructure Project

This project demonstrates Infrastructure as Code (IaC) using Terraform and Ansible to deploy and configure a highly available web application on AWS.

## Project Structure

```
.
├── ansible/
│   └── user-data-ansible.sh    # Bootstrap script for Ansible control node
└── terraform/
    ├── alb.tf                  # Application Load Balancer configuration
    ├── EC2.tf                  # EC2 instances configuration
    ├── keypair.tf             # SSH key pair configuration
    ├── network.tf             # VPC, subnets, and routing configuration
    ├── outputs.tf             # Terraform output variables
    ├── providers.tf           # AWS provider configuration
    ├── sg.tf                  # Security groups configuration
    └── variables.tf           # Input variables definition
```

## Infrastructure Components

### Terraform Configuration (/terraform)
- **VPC Setup**: Creates a VPC with public and private subnets across two availability zones
- **Network Components**: 
  - Internet Gateway for public subnets
  - NAT Gateway for private subnet internet access
  - Route tables for public and private subnets
- **Compute Resources**:
  - 1 Ansible control node in public subnet
  - 2 Application servers in private subnets
- **Load Balancing**:
  - Application Load Balancer (ALB)
  - Target groups and health checks
- **Security**:
  - Security groups for ALB, Ansible, and application instances
  - SSH key pair for instance access

### Ansible Configuration (/ansible)
- **Bootstrap Script**: Sets up Ansible control node with:
  - Ansible core installation
  - Python requirements
  - Inventory configuration
  - Default playbook for application deployment

## Prerequisites
- Terraform >= 1.0
- AWS CLI configured with appropriate credentials
- AWS Account with required permissions
- Git installed

## Getting Started

### Initialize and Deploy Infrastructure

1. Clone the repository
2. update the vars in \terraform\variables.tf
  aws_access_key_id
  aws_secret_access_key
  aws_session_token
  ip-address
3. in the \terraform folder
```powershell
terraform init
```
4. 
```powershell
terraform apply 
```