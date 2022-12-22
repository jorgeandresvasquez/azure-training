# Identity and Access Management for Azure

## Azure AD B2C

- Azure Active Directory B2C provides business-to-customer identify as a service.  Your customers user their preferred social, enterprise, or local account identities to get SSO access to your applications and apis.
- First 50,000 MAU (Monthly Active Users) are completely free
- You want your customers to be disconnected but adjacent to your Active Directory infrastructure
- Steps:
  1. Create an AD B2C Tenant
  1. Link and existing Azure AD B2C Tenant to my Azure Subscription

## Azure AD Domain Services (Azure AD DS)
- Azure AD Domain Services (Azure AD DS) provides managed domain services such as domain join, group policy, ligthweight directory access protocol (LDAP), and Kerberos/NTLM authentication that is fully compatible with Windows Server Active Directory.  You use these domain services wihtoug the need to deploy, manage, and patch domain controllers in the cloud.

## Azure AD Connect
- Azure AD Connect is the Microsoft tool designed to meet and accomplish your hybrid identity tools. When with Azure AD, your users are more productive because there's a common identity to access both cloud and on-premises resources

## Users and Groups
- The building blocks of Identity, Identity Management, and Access Control
- Users are not only humans, but machines and even applications
- Groups are used to group access, and are not limited to grouping the same types of accounts

## Enterprise Applications
- Azure AD has a gallery that contains thousands of applications that have been pre-integrated for single sign-on with Azure AD.
- Application proxy:  Azure AD acts as man-in-the-middle for authentication (Adds logging, tracking, etc.)

## App Registrations
- When building yor own line-of-business applications, you can integrate them with Azure AD to support single sign-on.  By registering your application with Azure AD, you have control over the authentication policy for the application.

## Managed Identities
- Before known as Managed Service Identities
- Azure Key Vault provides a way to securely store credentials, secrets, and other keys, but your code must authenticate to key Vault to retrieve them.  the managed identities for Azure resources feature in Azure Active Directory (Azure AD) solves this problem.  The feature provides Azure services with an automatically managed identity in Azure AD. You can use the identity to authenticate to any service that supports Azure AD authentication, including Key Vault, without any credentials in your code.

## Identity Governance
- Azure Active Directory (Azure AD) Identity Governance allows you to balance your organization's need for security and employee productivity with the right processes and visibiliy.  It provides you with capabilities to ensure that the right people have the right access to the right resources.

## Azure AD Conditional Access
- Conditional Access is the tool used by Azure Active Directory to bring signals together, to make decisions, and enforce organizational policies.  
- At their simplest they are if-then statements, if a user want to access a resource, then they must complete an action.

## Azure AD Privileged Identity Management (PIM)
- PIM provides time-based and approval-based role activation to mitigate the risks of excessive, unnecesary, or misused access permissions on resources that you care about.
