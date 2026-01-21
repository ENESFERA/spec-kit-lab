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

## Step 4: Implement Infrastructure Using Spec Kit Workflow

For each infrastructure component, follow the complete Spec Kit workflow:

1. **Specify** → Create the infrastructure specification
2. **Plan** → Generate implementation plan
3. **Tasks** → Break down into actionable tasks
4. **Implement** → Execute the implementation

> **⚠️ Important:** Complete the full workflow for each module before moving to the next one. This ensures proper dependency management.

---

### 📋 Recommended Implementation Order

| Order | Module                  | Reason                            |
| ----- | ----------------------- | --------------------------------- |
| 1     | Core Infrastructure     | Foundation for all resources      |
| 2     | Security Infrastructure | Key Vault needed by other modules |
| 3     | Backend Infrastructure  | API deployment                    |
| 4     | Frontend Infrastructure | Static web app                    |
| 5     | CI/CD Infrastructure    | Automation (Optional)             |

---

### Module 1: Core Infrastructure

#### Step 4.1.1 - Specify

```
/speckit.specify Create core Azure infrastructure with:
- Resource Group for all adventure game resources
- Virtual Network with subnets for app tier and database tier
- Network Security Groups with appropriate rules
- Storage Account for Terraform state (if not exists)
- Tags for environment, project name, and cost center
```

> **📝 Review:** Check the generated specification. Verify network topology, NSG rules, and tagging requirements are defined.

#### Step 4.1.2 - Plan

```
/speckit.plan Use Terraform 1.5+ with Azure provider. Create a networking module with VNet, subnets, and NSGs. Use variable files for dev and prod environments. Store state in Azure Storage with state locking. Follow Terraform best practices for naming.
```

> **📝 Review:** Verify the plan includes module structure, variable files, and state backend configuration.

#### Step 4.1.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover provider configuration, resource group, VNet, subnets, and NSGs.

#### Step 4.1.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Check generated Terraform files for proper naming, tagging, and NSG rules.

#### ✅ Checkpoint: Verify Core Infrastructure

```bash
cd terraform/environments/dev
terraform init
terraform plan
terraform apply

# Verify resources
az resource list --resource-group adventure-game-dev-rg --output table
```

#### 🔀 Git: Commit and Merge Module 1

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G` / `Cmd+Shift+G`)
2. Review changed files in the "Changes" section
3. Click `+` next to each file (or `+` on "Changes" header to stage all)
4. Enter commit message: `infra: implement core Azure infrastructure`
5. Click **Commit** button (checkmark icon)
6. Click **Sync Changes** or **Push** in the status bar

**Option B: Using Terminal**

```bash
git add .
git commit -m "infra: implement core Azure infrastructure

- Add Resource Group with proper tagging
- Create Virtual Network with app and database subnets
- Configure Network Security Groups
- Set up Terraform state backend"

git push origin main
```

---

### Module 2: Security Infrastructure

#### Step 4.2.1 - Specify

```
/speckit.specify Create security infrastructure:
- Azure Key Vault with access policies
- Managed Identities for services
- Private endpoints for database (optional)
- Diagnostic settings for audit logging
- Azure Defender recommendations compliance
```

> **📝 Review:** Check that the specification includes access policy definitions and logging requirements.

#### Step 4.2.2 - Plan

```
/speckit.plan Continue with the existing Terraform setup. Create a key-vault module. Implement access policies using managed identities. Add diagnostic settings for logging. Use data sources to reference the networking module outputs.
```

> **📝 Review:** Verify the plan includes managed identity integration and module dependencies.

#### Step 4.2.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover Key Vault creation, access policies, and diagnostic settings.

#### Step 4.2.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Check access policies, managed identity references, and diagnostic settings configuration.

#### ✅ Checkpoint: Verify Security Infrastructure

```bash
terraform plan
terraform apply

# Verify Key Vault
az keyvault show --name adventure-kv-dev --resource-group adventure-game-dev-rg
```

#### 🔀 Git: Commit and Merge Module 2

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `infra: implement security infrastructure`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "infra: implement security infrastructure

- Add Azure Key Vault with access policies
- Configure Managed Identities
- Set up diagnostic settings for logging
- Implement private endpoints (optional)"

git push origin main
```

---

### Module 3: Backend Infrastructure

#### Step 4.3.1 - Specify

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

> **📝 Review:** Check that the specification includes App Service settings, database configuration, and monitoring.

#### Step 4.3.2 - Plan

```
/speckit.plan Continue with the existing Terraform setup. Create app-service and database modules. Configure App Service with managed identity. Store connection string in Key Vault. Add Application Insights for monitoring. Use references to networking and key-vault modules.
```

> **📝 Review:** Verify the plan includes module dependencies, Key Vault secret references, and App Insights integration.

#### Step 4.3.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover App Service, PostgreSQL, Key Vault secrets, and Application Insights.

#### Step 4.3.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Check App Service configuration, database settings, managed identity, and Key Vault references.

#### ✅ Checkpoint: Verify Backend Infrastructure

```bash
terraform plan
terraform apply

# Verify App Service
az webapp show --name adventure-api-dev --resource-group adventure-game-dev-rg --query state

# Verify Database
az postgres flexible-server show --name adventure-db-dev --resource-group adventure-game-dev-rg
```

#### 🔀 Git: Commit and Merge Module 3

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `infra: implement backend infrastructure`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "infra: implement backend infrastructure

- Add App Service Plan and App Service
- Create PostgreSQL Flexible Server
- Store connection string in Key Vault
- Configure Application Insights
- Set up managed identity"

git push origin main
```

---

### Module 4: Frontend Infrastructure

#### Step 4.4.1 - Specify

```
/speckit.specify Create infrastructure for the frontend application:
- Azure Static Web App for the frontend
- CDN profile for global content delivery (optional)
- Custom domain configuration (optional)
- Environment variables for API URL
- Staging environment for preview deployments
```

> **📝 Review:** Check that the specification includes environment configuration and staging setup.

#### Step 4.4.2 - Plan

```
/speckit.plan Continue with the existing Terraform setup. Create static-web-app module. Configure environment variables to point to the App Service URL. Set up staging environment. Use outputs from the backend module for API URL.
```

> **📝 Review:** Verify the plan includes API URL configuration and module output references.

#### Step 4.4.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover Static Web App, environment variables, and staging configuration.

#### Step 4.4.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Check Static Web App configuration, API URL environment variable, and staging setup.

#### ✅ Checkpoint: Verify Frontend Infrastructure

```bash
terraform plan
terraform apply

# Get Static Web App URL
terraform output static_web_app_url
```

#### 🔀 Git: Commit and Merge Module 4

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `infra: implement frontend infrastructure`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "infra: implement frontend infrastructure

- Add Azure Static Web App
- Configure API URL environment variable
- Set up staging environment
- Add CDN profile (optional)"

git push origin main
```

---

### Module 5: CI/CD Infrastructure (Optional)

#### Step 4.5.1 - Specify

```
/speckit.specify Create CI/CD infrastructure:
- Service Principal for GitHub Actions
- Role assignments with minimum required permissions
- Azure Container Registry (if using containers)
- GitHub Actions secrets configuration guide
```

> **📝 Review:** Check that the specification includes role definitions and secrets documentation.

#### Step 4.5.2 - Plan

```
/speckit.plan Continue with the existing Terraform setup. Create Service Principal with Contributor role scoped to resource group. Document required GitHub secrets. Generate deployment token for Static Web App.
```

> **📝 Review:** Verify the plan includes role scope, secrets list, and deployment token generation.

#### Step 4.5.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover Service Principal, role assignments, and secrets documentation.

#### Step 4.5.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Check Service Principal configuration, role assignments, and generated documentation.

#### ✅ Checkpoint: Verify CI/CD Infrastructure

```bash
terraform plan
terraform apply

# Verify Service Principal
az ad sp list --display-name adventure-game-github-sp --output table
```

#### 🔀 Git: Commit and Merge Module 5

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `infra: implement CI/CD infrastructure`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "infra: implement CI/CD infrastructure

- Create Service Principal for GitHub Actions
- Configure role assignments
- Document required GitHub secrets
- Generate deployment tokens"

git push origin main
```

---

## Step 5: Deploy Complete Infrastructure

After implementing all modules, deploy the complete infrastructure:

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

## Step 6: Verify Deployment

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
