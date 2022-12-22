# Random Stuff to Memorize

- To resize VMs in the same availability set they must be resized together by stopping them all.
- How to use cloud-init to customize a Linux virtual machine in Azure on first boot
  - Reference:
    - https://learn.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-automate-vm-deployment
  - Cloud-init is a widely used approach to customize a Linux VM as it boots for the first time.
  - You can use cloud-init to install packages and write files, or to configure users and security. 
  - As cloud-init runs during the initial boot process, there are no additional steps or required agents to apply your configuration.
  - create a file named cloud-init.txt 
  - Now create a VM with az vm create. Use the --custom-data parameter to pass in your cloud-init config file.
    ```sh
        az vm create \
        --resource-group myResourceGroupAutomate \
        --name myAutomatedVM \
        --image UbuntuLTS \
        --admin-username azureuser \
        --generate-ssh-keys \
        --custom-data cloud-init.txt
    ```
- From the resource group blade you can go to Settings...Deploymnents and access ARM templates for all resources deployed within that RG.
- Azure Managed disks within VMs
  - Each virtual machine in your availability set is assigned an update domain and a fault domain by the underlying Azure platform.
  - Managed disks offer two different kinds of encryption. The first is Server Side Encryption (SSE), which is performed by the storage service. The second one is Azure Disk Encryption (ADE), which you can enable on the OS and data disks for your VMs.
  - There are three main disk roles in Azure: the data disk, the OS disk, and the temporary disk. These roles map to disks that are attached to your virtual machine.
  - There are three main disk roles in Azure: the data disk, the OS disk, and the temporary disk. These roles map to disks that are attached to your virtual machine.
  - On Azure Linux VMs, the temporary disk is typically /dev/sdb and on Windows VMs the temporary disk is D: by default.
- What is platformFaultDomainCount property in Azure Availability Set
  - The platformFaultDomainCount is a property that defines how many fault domains there are in the availability set. The upper limit is 2-3 (depends on a region).  If the platformFaultDomainCount is set to 3 (and the region supports 3 fault domains) and you have 15 virtual machines in the availability set, it means that 5 VMs can fail and become unavailable at a time, but the remaining 10 VMs are always available.
- Availability Sets Overview
  - https://learn.microsoft.com/en-us/azure/virtual-machines/availability-set-overview
  - Each virtual machine in your availability set is assigned an update domain and a fault domain by the underlying Azure platform. Each availability set can be configured with up to 3 fault domains and 20 update domains.
  - These configurations can't be changed once the availability set has been created. 
  - Update domains indicate groups of virtual machines and underlying physical hardware that can be rebooted at the same time.
  - Fault domains define the group of virtual machines that share a common power source and network switch. By default, the virtual machines configured within your availability set are separated across up to three fault domains.
  - Only one update domain is rebooted at a time.
  - A rebooted update domain is given 30 minutes to recover before maintenance is initiated on a different update domain.
- Azure AD built-in-roles
  - https://learn.microsoft.com/en-us/azure/active-directory/roles/permissions-reference
  - Global Reader role
    - Can read everything that a Global Administrator can, but not update anything.
  - Global Administrator
    - Can manage all aspects of Azure AD and Microsoft services that use Azure AD identities.
- Overview of DNS Zones and Records
  - To start hosting your domain in Azure DNS, you need to create a DNS zone for that domain name. Each DNS record for your domain is then created inside this DNS zone.
  - For example, the domain 'contoso.com' may contain several DNS records, such as 'mail.contoso.com' (for a mail server) and 'www.contoso.com' (for a web site).
  - A fully qualified domain name (FQDN) includes the zone name, whereas a relative name does not. For example, the relative record name www in the zone contoso.com gives the fully qualified record name www.contoso.com.
  - An apex record is a DNS record at the root (or apex) of a DNS zone. For example, in the DNS zone contoso.com, an apex record also has the fully qualified name contoso.com (this is sometimes called a naked domain). By convention, the relative name '@' is used to represent apex records.
  - https://learn.microsoft.com/en-us/azure/dns/dns-zones-records
  - Azure DNS manages all DNS records using record sets. A record set (also known as a resource record set) is the collection of DNS records in a zone that have the same name and are of the same type.
- From one tenant you can export custom roles as json and then imported into another tenant
- Understanding CIDR Notation when designing Azure Virtual Networks and Subnets
  - https://devblogs.microsoft.com/premier-developer/understanding-cidr-notation-when-designing-azure-virtual-networks-and-subnets/
- Azure service for post deployment configuration and automation tasks on Azure Virtual Machines
  - Use Azure Virtual machine extensions
- Ruby and Python can only run on Linux App Service Plans
- The Boot diagnostics feature does not support premium storage account or Zone Redundant Storage Account Types. If you use the premium storage account for Boot diagnostics, you might receive the StorageAccountTypeNotSupported error when you start the VM. 
- AKS
    ```bash
    > az provider register --namespace Microsoft.OperationsManagement
    > az provider register --namespace Microsoft.OperationalInsights
    > az group create --name myResourceGroup --location eastus
    > az aks create -g myResourceGroup -n myAKSCluster --enable-managed-identity --node-count 1 --enable-addons monitoring   --enable-msi-auth-for-monitoring  --generate-ssh-keys
    > az aks install-cli (install kubecctl)
    > az aks get-credentials --resource-group myResourceGroup --name myAKSCluster (downloads credentials to ~/.kube/config)
    > kubectl apply -f azure-vote.yaml
    > kubectl get service azure-vote-front --watch
    > az group delete --name myResourceGroup --yes --no-wait
    ```
- Azure built-in roles
  -  https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles
- AD Application and Service Account
  - Going back to the user analogy, after creating a user, you often need to grant them permissions to areas in your network.  To do this for an Azure AD application, you create a service principal object.  The service principal defines the access policy and permissions for the application in a tenant.  So, an Azure AD application is like a user (with an ID and password), and a service principal object is like the user's level of access.
- Activity Logs are kept for 90 day
- In Alerts/Action Groups notifications and Actions are different things
  - Notifications configure the method in which users will be notified when the action group triggers.
  - Actions configure the method in which actions are performed when the action group triggers.
- Signal Types in Alerts can be metrics, log search queries or activity logs
- Network Watcher
  - Network Watcher is a regional service that enables you to monitor and diagnose conditions at a network scenario level.
- self-service password reset (SSPR).
  - You can configure SSPR registration by group or for all domain users. You cannot configure SSPR registration by user.
- By default, the data in a Log Analytics workspace is retained for 30 days.
- Naming convention for Azure PowerShell Cmdlets:  {verb}-Az{noun}
  - If your cmdlet is performing a PATCH operation (i.e., a partial replacement on the server), then the cmdlet should use the verb Update.
  - If your cmdlet is performing a PUT operation (i.e., a full replacement on the server), the cmdlet should use the verb Set.
  - Attributes:
    - ResourceId
    - ResourceGroupName
- Azure AD:
  - Adding a group to an administrative unit brings the group itself into the management scope of the administrative unit, but not the members of the group. In other words, an administrator scoped to the administrative unit can manage properties of the group, such as group name or membership, but they cannot manage properties of the users or devices within that group (unless those users and devices are separately added as members of the administrative unit).
- Backup
  - DPM 
    - System Center Data Protection Manager (DPM) is a robust enterprise backup and recovery system that contributes to your BCDR strategy by facilitating the backup and recovery of enterprise data.
  - Recovery Services Vault vs Backup vault
    - Backup vaults are the older versions. Recovery Services vaults are the current version. This is based on the Azure Service Manager
    - By default, your Recovery Services vault has geo-redundant storage. If you are using Azure as a primary backup storage endpoint, use the default geo-redundant storage. If you are using Azure as a non-primary backup storage endpoint, then choose locally redundant storage, which will reduce the cost of storing data in Azure.
    - The Azure VM Agent must be installed on the Azure virtual machine for the Backup extension to work. However, if your VM was created from the Azure gallery, then the VM Agent is already present on the virtual machine
  - Another method of backing up virtual machines is using a Data Protection Manager (DPM) or Microsoft Azure Backup Server (MABS) server. This method can be used for specialized workloads, virtual machines, or files, folders, and volumes. Specialized workloads can include SharePoint, Exchange, and SQL Server.
  - Azure Backup uses the Microsoft Azure Recovery Services (MARS) agent to back up and recover files, folders, and the volume or system state from an on-premises computer to Azure.
- Azure App Service
  - Enables you to build and host web apps, mobil back ends, and restful APIs in the programming language of your choice without managing infrastructure
  - Associated to App Service Plan
    - Is a container capacity with vCore, RAM, Storage
    - You can scale up and out
- Moving resources
  - Moving a resource only moves it to a new resource group or subscription. It doesn't change the location of the resource.
  - When you move a resource, you change its resource ID. The standard format for a resource ID is /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/{resourceProviderNamespace}/{resourceType}/{resourceName}. When you move a resource to a new resource group or subscription, you change one or more values in that pat
  - When you move a resource, you change its resource ID. The standard format for a resource ID is /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/{resourceProviderNamespace}/{resourceType}/{resourceName}. When you move a resource to a new resource group or subscription, you change one or more values in that path
  - The source and destination subscriptions must exist within the same Azure Active Directory tenant.
  - The destination subscription must be registered for the resource provider of the resource being moved.
  - For a move across subscriptions, the resource and its dependent resources must be located in the same resource group and they must be moved together.
- Locks
  - Scope
    - Azure control plane operations go to https://management.azure.com. Azure data plane operations go to your service instance, such as https://myaccount.blob.core.windows.net/.
    - The distinction means locks protect a resource from changes, but they don't restrict how a resource performs its functions. A ReadOnly lock, for example, on an SQL Database logical server, protects it from deletions or modifications. It allows you to create, update, or delete data in the server database. Data plane operations allow data transactions.
- CanNotDelete means authorized users can still read and modify a resource, but they can't delete the resource
- ReadOnly means authorized users can read a resource, but they can't delete or update the resource. Applying this lock iss similar to restricting all authorized users to the permissions granted by the Reader role.
- Availability Sets
  - Udpate Domain
    - Each update domain contains a set of virtual machines and associated physical hardware that can be updated and rebooted at the same time.
    - By default, there are five (non-user-configurable) update domains.
    - You can configure up to 20 update domains.
  - Fault Domain
    - A fault domain defines a group of virtual machines that share a common set of hardware (or switches) that share a single point of failure. An example is a server rack serviced by a set of power or networking switches.
- Scale Sets
  - Azure Virtual Machine Scale Sets are an Azure Compute resource that you can use to deploy and manage a set of identical virtual machines. When you implement Virtual Machine Scale Sets and configure all your virtual machines in the same way, you gain true autoscaling. Virtual Machine Scale Sets automatically increases the number of your virtual machine instances as application demand increases, and reduces the number of machine instances as demand decreases.
  - Virtual Machine Scale Sets support the use of Azure Load Balancer for basic layer-4 traffic distribution, and Azure Application Gateway for more advanced layer-7 traffic distribution and SSL termination.