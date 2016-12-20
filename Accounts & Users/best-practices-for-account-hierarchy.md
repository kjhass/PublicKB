{{{
  "title": "Best Practices for Account Hierarchy Management",
  "date": "3-31-2015",
  "author": "Dave Burkhardt",
  "attachments": [],
  "contentIsHTML": false
}}}

### Overview
CenturyLink Cloud’s Account Hierarchy management feature allows customers granular enablement and demarcation of users, systems, groups, networks, billing, reporting, and/or sub-accounts that reside within the CenturyLink platform. Customers with administrator access can create and manage these attributes in the Control Portal. It is strongly recommended that organizations consider the following factors, limitations, and best practices before they leverage these features.

### Factors that Influence Account Configuration
There are many factors that influence how a customer or reseller configure their accounts.
* User Access Controls (control who can access which resources)
* Invoice Separation (each account and/or sub-account will either get its own invoice
  or be grouped by account)
* Network Access Controls (network data flow to and/or from Sub Accounts)
* Reporting (report based on hierarchy)
* Partner: Custom pricing (inherited based on hierarchy)
* Partner: Branding (inherited based on hierarchy)
* Resource Governing (limit the number of resources consumed)
* Operations and Management (policies are inherited, Blueprints can be run against a group)

### Limitations
* Accounts cannot be moved within their hierarchies
* There is no “read-only” mode for users or role cascades, so be careful about allowing access
* Billing data out of Savvis/CenturyLink does not go down to server level, only Account and/or Group
* Additional detail about current spend can be found in the portal or through the API, but API data for invoices is not guaranteed to be aligned with Savvis/CenturyLink data (e.g. no tax)
* There is no self-service ability to set custom pricing in the Control Portal

### Best Practices
Design your account hierarchy before you add users or provision resources. Here are some aspects to consider with your design:
* Do you need to create sub accounts for creating administrative boundaries and/or isolating costs for charge backs and/or reselling of services? If so, designing your account hierarchy to meet your business goals is a critical first step.
* Does if it matter which data center will be your primary location? We typically see customers deploy servers in their default data center, while neglecting to consider other locations.
* Will there be any specific data center locations for which you want to prevent your users from being able to deploy resources?
* Do you need certain users to only have access to specific accounts? If so, add these users to a child/sub account.
* Does your organization want to mark-up CenturyLink services to other departments or customers (e.g., reseller)? Add a child account to your parent account and work with CenturyLink's noc to mark-up the child accounts.
* Do you need to block or enable network access between accounts and/or do you need to consider specific data flows between separate accounts? Run an end-to-end process test with the data you need to make sure the solution will work. For example, the account hierarchy listed below could be designed as follows:
    * All VLANs/accounts can reach the backoffice account since it has the Active Directory, DNS, etc.
    * Only the backoffice account will be able to access the Internet; your organization sets policies restricting Internet access directly from all other accounts and/or VLANs
    * Load Balancers can be placed on the backoffice account and/or VLANs; the web servers in the Market account and/ or VLAN need to use these LBs for their web app
    * The IT Intranet and Help Desk accounts and/or VLANs will be restricted to only access each other

![Account Structure]../images/acct-structure1.png)


### For additional information, please reference the following articles:
https://www.ctl.io/knowledge-base/accounts-&-users/account-hierarchy-user-network-and-firewall-policy-primer/
https://www.ctl.io/knowledge-base/accounts-&-users/creating-a-sub-account/
