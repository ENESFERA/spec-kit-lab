# ☁️ Lab 3: The Plane of the Kingdom

## Infrastructure as Code with Terraform and GitHub Spec Kit

### Overview

In this final challenge, you will invoke the arcane art of **Infrastructure as Code** using **Terraform** to deploy your adventure game to the **Azure** cloud realm. You will use GitHub Spec Kit to specify and plan your infrastructure before implementation.

**Estimated Time:** 1.5-2 hours

**Technologies:**

- **Terraform** for Infrastructure as Code
- **Azure** cloud platform
- Development Methodology: **Spec-Driven Development (SDD)**

---

## Prerequisites

Before starting this lab, ensure you have:

- [ ] Completed Lab 1 (REST API) and Lab 2 (Frontend)
- [ ] Azure account with an active subscription
- [ ] Azure CLI installed (`az --version`)
- [ ] Terraform installed (`terraform --version`)
- [ ] **Visual Studio Code** installed
- [ ] **GitHub Copilot** extension installed and activated in VS Code
- [ ] The Spec Kit CLI installed

---

## Step 1: Install and Configure Tools

### Install Terraform

```bash
# On Ubuntu/Debian
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common
wget -O- https://apt.releases.hashicorp.com/gpg | \
  gpg --dearmor | \
  sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
  https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
  sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt-get install terraform

# Verify installation
terraform --version
```

### Configure Azure CLI

```bash
# Login to Azure
az login

# Set your subscription (if you have multiple)
az account set --subscription "Your Subscription Name"

# Verify
az account show
```

---

## Step 2: Initialize Your Infrastructure Project

Create a new Spec Kit project for infrastructure:

```bash
# Initialize the project
specify init adventure-infra --ai copilot

# Navigate to your project
cd adventure-infra

# Create Terraform directory structure
mkdir -p terraform/modules
mkdir -p terraform/environments/{dev,prod}
```

---

## 💬 Using Spec Kit Commands in VS Code

All `/speckit.*` commands are executed through the **GitHub Copilot Chat panel** in VS Code:

1. **Open the Chat Panel**: Press `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Shift+I` (Mac), or click the Copilot icon in the sidebar
2. **Type the command**: Enter the `/speckit.*` command followed by your description
3. **Press Enter**: Copilot will process the command and generate the appropriate files
4. **Review the output**: Check the generated specifications and approve any file changes

> **💡 Tip:** Make sure you have the project folder open in VS Code before running commands. The commands work on the current workspace.

---

## Step 3: Establish Infrastructure Principles

Define the guiding principles for your infrastructure:

```
/speckit.constitution Create principles for Azure infrastructure deployment:
- Security by default: All resources must have minimum required permissions
- Network isolation: Use Virtual Networks and subnets appropriately
- Secrets management: Never hardcode secrets; use Azure Key Vault
- Cost awareness: Use appropriate SKUs for dev/prod environments
- Modularity: Create reusable Terraform modules
- State management: Use remote state with Azure Storage
- Tagging: All resources must have environment, project, and owner tags
- Documentation: Every module must have README and variable descriptions
```

---

## Step 4: Create Infrastructure Specifications

### 4.1 Core Infrastructure Specification

```
/speckit.specify Create core Azure infrastructure with:
- Resource Group for all adventure game resources
- Virtual Network with subnets for app tier and database tier
- Network Security Groups with appropriate rules
- Azure Key Vault for secrets management
- Storage Account for Terraform state (if not exists)
- Tags for environment, project name, and cost center
```

### 4.2 Backend Infrastructure Specification

```
/speckit.specify Create infrastructure for the REST API backend:
- Azure App Service Plan (Linux, appropriate tier for environment)
- Azure App Service for the API application
- Azure Database for PostgreSQL Flexible Server
- Connection string stored in Key Vault
- App Service configured with managed identity
- Application Insights for monitoring
- Custom domain and SSL certificate (optional)
```

### 4.3 Frontend Infrastructure Specification

```
/speckit.specify Create infrastructure for the frontend application:
- Azure Static Web App for the frontend
- CDN profile for global content delivery (optional)
- Custom domain configuration (optional)
- Environment variables for API URL
- Staging environment for preview deployments
```

### 4.4 Security Infrastructure Specification

```
/speckit.specify Create security infrastructure:
- Azure Key Vault with access policies
- Managed Identities for services
- Private endpoints for database (optional)
- Azure Front Door or Application Gateway (optional)
- Diagnostic settings for audit logging
- Azure Defender recommendations compliance
```

### 4.5 CI/CD Infrastructure Specification (Optional)

```
/speckit.specify Create CI/CD infrastructure:
- Service Principal for GitHub Actions
- Role assignments with minimum required permissions
- Azure Container Registry (if using containers)
- GitHub Actions secrets configuration guide
```

---

## Step 5: Create Implementation Plan

Generate the technical implementation plan:

```
/speckit.plan Use Terraform 1.5+ with Azure provider. Create modules for: networking, app-service, database, key-vault, static-web-app. Use variable files for dev and prod environments. Store state in Azure Storage with state locking. Use data sources to reference existing resources. Follow Terraform best practices for naming and structure.
```

---

## Step 6: Analyze Infrastructure Plan

Validate your infrastructure design:

```
/speckit.analyze
```

Check for:

- Security gaps
- Missing dependencies
- Cost optimization opportunities

---

## Step 7: Generate Task Breakdown

Create actionable infrastructure tasks:

```
/speckit.tasks
```

---

## Step 8: Execute Implementation

Build the Terraform configuration:

```
/speckit.implement
```

The AI will create:

1. Module structure
2. Variable definitions
3. Resource configurations
4. Output definitions
5. Environment-specific configurations

---

## Step 9: Deploy Infrastructure

### Initialize Terraform

```bash
cd terraform/environments/dev

# Initialize Terraform
terraform init

# Validate configuration
terraform validate

# Format check
terraform fmt -check -recursive
```

### Plan Deployment

```bash
# Create execution plan
terraform plan -out=tfplan

# Review the plan carefully!
```

### Apply Infrastructure

```bash
# Apply the plan
terraform apply tfplan

# Note the outputs
terraform output
```

---

## Step 10: Verify Deployment

### Check Azure Resources

```bash
# List resources in resource group
az resource list --resource-group adventure-game-dev-rg --output table

# Check App Service status
az webapp show --name adventure-api-dev --resource-group adventure-game-dev-rg --query state

# Test database connectivity
az postgres flexible-server show --name adventure-db-dev --resource-group adventure-game-dev-rg
```

### Test Application Deployment

```bash
# Get the App Service URL
API_URL=$(terraform output -raw api_url)
echo "API URL: $API_URL"

# Test health endpoint
curl "$API_URL/health"
```

---

## Required Terraform Structure

Your project should follow this structure:

```
terraform/
├── modules/
│   ├── networking/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   └── README.md
│   ├── app-service/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   └── README.md
│   ├── database/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   └── README.md
│   ├── key-vault/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   └── README.md
│   └── static-web-app/
│       ├── main.tf
│       ├── variables.tf
│       ├── outputs.tf
│       └── README.md
├── environments/
│   ├── dev/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── terraform.tfvars
│   │   ├── outputs.tf
│   │   └── backend.tf
│   └── prod/
│       ├── main.tf
│       ├── variables.tf
│       ├── terraform.tfvars
│       ├── outputs.tf
│       └── backend.tf
└── README.md
```

---

## Security Checklist

Ensure your infrastructure implements:

- [ ] **Network Security**
  - [ ] Virtual Network isolation
  - [ ] Network Security Groups with restrictive rules
  - [ ] No public IP for database

- [ ] **Identity & Access**
  - [ ] Managed Identities for services
  - [ ] Minimum required permissions
  - [ ] Key Vault for secrets

- [ ] **Data Protection**
  - [ ] Database encryption at rest
  - [ ] SSL/TLS for all connections
  - [ ] Secure connection strings

- [ ] **Monitoring & Compliance**
  - [ ] Diagnostic settings enabled
  - [ ] Application Insights configured
  - [ ] Resource tagging

---

## Minimum Infrastructure Requirements Checklist

Ensure your Terraform code includes:

- [ ] **Modules**
  - [ ] At least 3 reusable modules
  - [ ] Each module has variables.tf and outputs.tf
  - [ ] Module documentation (README.md)

- [ ] **State Management**
  - [ ] Remote state configuration
  - [ ] State locking enabled
  - [ ] Separate state per environment

- [ ] **Resource Configuration**
  - [ ] Resource Group
  - [ ] App Service or Container App
  - [ ] Database service
  - [ ] Key Vault

- [ ] **Environment Support**
  - [ ] Dev environment configuration
  - [ ] Variables for environment differences
  - [ ] Appropriate SKUs per environment

- [ ] **Documentation**
  - [ ] Main README with setup instructions
  - [ ] Variable descriptions
  - [ ] Output descriptions

---

## Example Module: App Service

```hcl
# modules/app-service/main.tf

resource "azurerm_service_plan" "main" {
  name                = var.service_plan_name
  resource_group_name = var.resource_group_name
  location            = var.location
  os_type             = "Linux"
  sku_name            = var.sku_name

  tags = var.tags
}

resource "azurerm_linux_web_app" "main" {
  name                = var.app_name
  resource_group_name = var.resource_group_name
  location            = var.location
  service_plan_id     = azurerm_service_plan.main.id

  site_config {
    application_stack {
      node_version = "18-lts"
    }
    always_on = var.always_on
  }

  identity {
    type = "SystemAssigned"
  }

  app_settings = var.app_settings

  tags = var.tags
}

# modules/app-service/variables.tf

variable "app_name" {
  description = "Name of the App Service"
  type        = string
}

variable "resource_group_name" {
  description = "Name of the resource group"
  type        = string
}

variable "location" {
  description = "Azure region for resources"
  type        = string
}

variable "service_plan_name" {
  description = "Name of the App Service Plan"
  type        = string
}

variable "sku_name" {
  description = "SKU for the App Service Plan"
  type        = string
  default     = "B1"
}

variable "always_on" {
  description = "Keep the app always running"
  type        = bool
  default     = false
}

variable "app_settings" {
  description = "Application settings"
  type        = map(string)
  default     = {}
}

variable "tags" {
  description = "Tags to apply to resources"
  type        = map(string)
  default     = {}
}

# modules/app-service/outputs.tf

output "app_service_id" {
  description = "ID of the App Service"
  value       = azurerm_linux_web_app.main.id
}

output "default_hostname" {
  description = "Default hostname of the App Service"
  value       = azurerm_linux_web_app.main.default_hostname
}

output "identity_principal_id" {
  description = "Principal ID of the managed identity"
  value       = azurerm_linux_web_app.main.identity[0].principal_id
}
```

---

## Evaluation Criteria

Your implementation will be evaluated on:

| Criteria                             | Weight |
| ------------------------------------ | ------ |
| Security Implementation              | 30%    |
| Documentation Quality                | 25%    |
| Best Practices (Modules, State, DRY) | 25%    |
| Successful Deployment                | 20%    |

---

## Tips for Success

1. **Start with State Backend** - Set up remote state first
2. **Build Modules Incrementally** - Test each module before combining
3. **Use terraform plan** - Always review before applying
4. **Tag Everything** - Makes cost tracking and cleanup easier
5. **Document Variables** - Future you will thank present you

---

## Cleanup

When you're done, clean up your resources:

```bash
# Destroy all resources
terraform destroy

# Confirm with 'yes'
```

---

## Resources

- [GitHub Spec Kit Documentation](https://speckit.org/)
- [Terraform Azure Provider Documentation](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)
- [Azure Well-Architected Framework](https://docs.microsoft.com/azure/architecture/framework/)
- [Terraform Best Practices](https://www.terraform-best-practices.com/)
- [Azure Naming Conventions](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging)

---

**May your infrastructure be immutable and your deployments reproducible! ☁️🏗️**
