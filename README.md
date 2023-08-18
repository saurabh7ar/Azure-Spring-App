# Azure-Spring

Azure Spring Apps makes it easy to deploy Spring applications to Azure without any code changes.
Azure Spring Apps provides lifecycle management using:
  comprehensive monitoring and diagnostics, 
  configuration management, 
  service discovery, 
  CI/CD integration, 
  blue-green deployments, and more.
  
# Reference Architecture
Refer - https://learn.microsoft.com/en-us/previous-versions/azure/spring-apps/reference-architecture?tabs=azure-spring-standard
![image](https://github.com/saurabh7ar/Azure-Spring-App/assets/132929888/ada460ed-2884-497f-be66-855f92cf59f4)

  - This reference architecure is a foundation using a typical Hub & Spoke design.
  - Azure Spring App is deployed in a single spoke that depends in shared serices hosted in the hub.

# Pre-Requisites
Azure Subscription
Install Terraform - https://developer.hashicorp.com/terraform/downloads
Two dedicated Subnets for the Azure Spring Apps cluster:
  Subnet 1 - This subnet will be used for service runtime
  Subnet 2 - This subnet will be used for the Spring applications
Virtual Network Requirements:
  The virtual network must reside in the same location as the Azure Spring Apps instance.
  The virtual network must be in the same subscription as the Azure Spring Apps instance.
An existing Log Analytics workspace for Azure Spring Apps diagnostics settings and a workspace-based Application Insights resource
Three internal Classless Inter-Domain Routing (CIDR) ranges (at least /16 each) that you've identified for use by the Azure Spring Apps cluster. These CIDR ranges won't be directly routable and will be used only internally by the Azure Spring Apps cluster. Clusters may not use 169.254.0.0/16, 172.30.0.0/16, 172.31.0.0/16, or 192.0.2.0/24 for the internal Azure Spring Apps CIDR. Clusters also may not use any IP ranges included within the cluster virtual network address range.
Service permission granted to the virtual network. The Azure Spring Apps Resource Provider requires Owner permission to your virtual network in order to grant a dedicated and dynamic service principal on the virtual network for further deployment and maintenance. Refer - https://learn.microsoft.com/en-us/azure/spring-apps/how-to-deploy-in-azure-virtual-network#grant-service-permission-to-the-virtual-network


# Ref - https://learn.microsoft.com/en-us/azure/spring-apps/quickstart-deploy-infrastructure-vnet-terraform?tabs=azure-spring-apps-standard
