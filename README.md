# Infrastructure in AWS using Terraform and Ansible

## Table of Contents

- [Project Description](#project-description)
- [Project structure](#project-structure)
- [Dependencies](#dependencies)
- [Installation and startup](#installation-and-startup)
- [Destroy](#destroy)
- [AWS Diagrams](#aws-diagrams)
- [State](#state)
- [Tree](#tree)

## Project Description

This project is an automated way to deploy infrastructure to Amazon Web Services (AWS) using Terraform to create resources and Ansible to configure them. The project uses Nginx as a load balancer and Apache as a web server.
Create file `<name>`.tfvars in main folder. Add next params (But before create User in AWS using AMI, shoud have access to EC2, VPC, SG).

## Project structure

- **/**: Terraform file directory.
  - `main.tf`: Terraform core file with resource definition.
  - `vars.tf`: Terraform variables.
  - `secrets.tfvars`: Terraform secret Variables.
  - `nginx.tmpl`: Template for nginx configurations.
  - `template.tmpl`: Template for ansible inventory.
  - `change_permission.sh`: Change permission for keys.
  - `/modules`: Modules for Terraform.
    In the secrets.tfvars, you need to specify the keys to the AWS user.
    Example:

```
access_key="your_value"
secret_key="your_value"
```

- **/ansible**: Catalog with Ansible configurations.
  - `inventory/hosts`: File with hosts information.
  - `web.yml`: Ansible core playbook.
  - `source`: Folder for nginx and html.
  - `roles`: Ansible roulse.

## Dependencies

Before you start using it, make sure you have the following tools installed:

- [Terraform](https://www.terraform.io/)
- [Ansible](https://www.ansible.com/)

## Installation and startup

```bash
   git clone https://github.com/Mikitasz/StaticWebApp-AWS-TERRAFORM-ANISBLE-NGINX
```

```bash
   cd StaticWebApp-AWS-TERRAFORM-ANISBLE-NGINX
```

```bash
   terraform init
   terraform plan -var-file=secrets.tfvars
   terraform aply -var-file=secrets.tfvars
```

```bash
   ansible-playbook -i ansible/inventory/hosts ansible/web.yaml 
```

## Destroy

```bash
   terraform destroy -var-file=secrets.tfvars
```

## AWS Diagrams

<img width="631" alt="s" src="https://github.com/Mikitasz/StaticWebApp-AWS-TERRAFORM-ANISBLE-NGINX/assets/94795099/24133ce8-8594-4b13-8260-8134d0e65389">

![Untitled Diagram drawio (8)](https://github.com/Mikitasz/StaticWebApp-AWS-TERRAFORM-ANISBLE-NGINX/assets/94795099/b256735d-f08f-4a0a-becf-343687a3d2aa)

## State

✅ Diagrams

✅ Terraform IaC

❌ Readability

✅ Ansible playbooks

❌ Autoscaling group

❌ CloudWatch

❌ Maximum automations

❌ Tests

✅ Final diagram

## Tree

```bash
.
├── README.md
├── ansible
│   ├── inventory
│   ├── roles
│   ├── source
│   └── web.yaml
├── change_permission.sh
├── main.tf
├── modules
│   ├── ASG
│   ├── NAT
│   ├── ansible_inventory
│   ├── bastion
│   ├── create key-pair
│   ├── ec2
│   ├── internet_gateway
│   ├── nginx
│   ├── route
│   ├── sg
│   └── vpc
├── nginx.tmpl
├── secrets.tfvars
├── template.tmpl
├── terraform.tfstate
├── terraform.tfstate.backup
└── vars.tf
```
