## Introduction

This document provides a step-by-step guide to create supporting services for the applications, including MySQL.

## Azure MySQL

[Azure Database for MySQL](https://azure.microsoft.com/en-us/services/mysql/) is a managed database service that allows you to run, manage, and scale highly available MySQL databases in the cloud. It offers built-in high availability, automated backups, and enterprise-grade security features. With Azure MySQL, you can focus on application development without worrying about database management.

## Prerequisites

- Follow [01-create-kubernetes-service](./01-create-kubernetes-service.md) to create Azure Kubernetes Service and Azure Container Registry.
- Azure CLI installed
- Azure subscription
- Sufficient permissions to create resources in the Azure subscription
  - **Contributor** - Creates resource and all other Azure resources
  - **User Access Administrator** - Assign necessary roles

## Outputs

- Azure MySQL

## Steps

### 1. Set Variables

Set up the variables used to create the MySQL:
```
source resources/var.sh
az account set -s ${SUBSCRIPTION}

echo "RESOURCE_GROUP=${RESOURCE_GROUP}"
echo "AKS_NAME=${AKS_NAME}"
echo "MYSQL_NAME=${MYSQL_NAME}"
```

### 2. Create MySQL

1. Create MySQL Flexible server and enable the access from Kubernetes
```
az mysql flexible-server create --resource-group ${RESOURCE_GROUP} --name ${MYSQL_NAME} --database-name ${MYSQL_DATABASE} --admin-user admin --admin-password '<admin-password>'
```

## Next Steps

- Follow [06-containerize-application](./06-containerize-application.md) to learn how to containerize your applications and push them to Azure Container Registry.