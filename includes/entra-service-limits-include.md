---
 title: Include file
 description: Include file
 author: rolyon
 ms.service: entra-id
 ms.topic: include
 ms.date: 07/15/2024
 ms.author: rolyon
 ms.custom: include file
---
Here are the usage constraints and other service limits for the Microsoft Entra service.

| Category | Limit |
| --- | --- |
| Tenants | <li>A single user can belong to a maximum of 500 Microsoft Entra tenants as a member or a guest. <li>Create a maximum of 200 tenants.<li>Limit of 300 [license-based subscriptions](/microsoft-365/commerce/licenses/subscriptions-and-licenses) (such as Microsoft 365 subscriptions) per tenant |
| Domains | <li>You can add no more than 5,000 managed domain names. <li>If you set up all of your domains for federation with on-premises Active Directory, you can add no more than 2,500 domain names in each tenant. |
|Resources |<ul><li>By default, a maximum of 50,000 Microsoft Entra resources can be created in a single tenant by users of the Microsoft Entra ID Free edition. If you have at least one verified domain, the default Microsoft Entra service quota for your organization is extended to 300,000 Microsoft Entra resources. <br>The Microsoft Entra service quota for organizations created by self-service sign-up remains 50,000 Microsoft Entra resources, even after you perform an internal admin takeover and the organization is converted to a managed tenant with at least one verified domain. This service limit is unrelated to the pricing tier limit of 500,000 resources on the Microsoft Entra pricing page. <br>To go beyond the default quota, you must contact Microsoft Support.</li><li>A non-admin user can create no more than 250 Microsoft Entra resources. Both active resources and deleted resources that are available to restore count toward this quota. Only deleted Microsoft Entra resources that were deleted fewer than 30 days ago are available to restore. Deleted Microsoft Entra resources that are no longer available to restore count toward this quota at a value of one-quarter for 30 days. <br>If you have developers who are likely to repeatedly exceed this quota in the course of their regular duties, you can [create and assign a custom role](../articles/active-directory/roles/quickstart-app-registration-limits.md) with permission to create a limitless number of app registrations.</li><li>Resource limitations apply to all directory objects in a given Microsoft Entra tenant, including users, groups, applications, and service principals.</li></ul> |
| Schema extensions |<ul><li>String-type extensions can have a maximum of 256 characters. </li><li>Binary-type extensions are limited to 256 bytes.</li><li>Only 100 extension values, across *all* types and *all* applications, can be written to any single Microsoft Entra resource.</li><li>Only User, Group, TenantDetail, Device, Application, and ServicePrincipal entities can be extended with string-type or binary-type single-valued attributes.</li></ul> |
| Applications | <ul><li>A maximum of 100 users and service principals can be owners of a single application.</li><li>A user, group, or service principal can have a maximum of 1,500 app role assignments. The limitation is on the service principal, user, or group across all app roles and not on the number of assignments on a single app role.</li><li>A user can have credentials configured for a maximum of 48 apps using password-based single sign-on. This limit only applies for credentials configured when the user is directly assigned the app, not when the user is a member of a group that is assigned.</li><li>A group can have credentials configured for a maximum of 48 apps using password-based single sign-on.</li><li>See more limits in [Validation differences by supported account types](../articles/active-directory/develop/supported-accounts-validation.md).</li></ul> |
|Application manifest |A maximum of 1,200 entries can be added to the application manifest.<br/>See more limits in [Validation differences by supported account types](../articles/active-directory/develop/supported-accounts-validation.md). |
| Groups |<ul><li>A non-admin user can create a maximum of 250 groups in a Microsoft Entra organization. Any Microsoft Entra admin who can manage groups in the organization can also create an unlimited number of groups (up to the Microsoft Entra object limit). If you assign a role to a user to remove the limit for that user, assign a less privileged, built-in role such as User Administrator or Groups Administrator.</li><li>A Microsoft Entra organization can have a maximum of 15,000 dynamic groups and dynamic administrative units combined.</li><li>A maximum of 500 [role-assignable groups](../articles/active-directory/roles/groups-concept.md) can be created in a single Microsoft Entra organization (tenant).</li><li>A maximum of 100 users can be owners of a single group.</li><li>Any number of Microsoft Entra resources can be members of a single group.</li><li>A user can be a member of any number of groups. When security groups are being used in combination with SharePoint Online, a user can be a part of 2,049 security groups in total. This includes both direct and indirect group memberships. When this limit is exceeded, authentication and search results become unpredictable.</li><li>By default, the number of members in a group that you can synchronize from your on-premises Active Directory to Microsoft Entra ID by using Microsoft Entra Connect is limited to 50,000 members. If you need to sync a group membership that's over this limit, you must onboard the [Microsoft Entra Connect Sync V2 endpoint API](../articles/active-directory/hybrid/how-to-connect-sync-endpoint-api-v2.md).</li><li>When you select a list of groups, you can assign a group expiration policy to a maximum of 500 Microsoft 365 groups. There is no limit when the policy is applied to all Microsoft 365 groups.</li></ul><br/> At this time, the following scenarios are supported with nested groups:<ul><li> One group can be added as a member of another group, and you can achieve group nesting.</li><li> Group membership claims. When an app is configured to receive group membership claims in the token, nested groups in which the signed-in user is a member are included.</li><li>Conditional access (when a conditional access policy has a group scope).</li><li>Restricting access to self-serve password reset.</li><li>Restricting which users can do Microsoft Entra join and device registration.</li></ul><br/>The following scenarios are *not* supported with nested groups:<ul><li> App role assignment, for both access and provisioning. Assigning groups to an app is supported, but any groups nested within the directly assigned group won't have access.</li><li>Group-based licensing (assigning a license automatically to all members of a group).</li><li>Microsoft 365 Groups.</li></ul> |
| Application Proxy | <ul><li>A maximum of 500 transactions\* per second per Application Proxy application.</li><li>A maximum of 750 transactions per second for the Microsoft Entra organization.<br><br>\*A transaction is defined as a single HTTP request and response for a unique resource. When clients are throttled, they'll receive a 429 response (too many requests). Transaction metrics are collected on each connector and can be monitored using performance counters under the object name `Microsoft AAD App Proxy Connector`. |
| Access Panel |There's no limit to the number of applications per user that can be displayed in the Access Panel, regardless of the number of assigned licenses.  |
| Reports | A maximum of 1,000 rows can be viewed or downloaded in any report. Any other data is truncated. |
| Administrative units | <ul><li>A Microsoft Entra resource can be a member of no more than 30 administrative units.</li><li>A maximum of 100 restricted management administrative units in a tenant.</li><li>A Microsoft Entra organization can have a maximum of 15,000 dynamic groups and dynamic administrative units combined.</li></ul> |
| Microsoft Entra roles and permissions | <ul><li>A maximum of 100 [Microsoft Entra custom roles](/azure/active-directory//users-groups-roles/roles-custom-overview?context=azure%2factive-directory%2fusers-groups-roles%2fcontext%2fugr-context) can be created in a Microsoft Entra organization.</li><li>A maximum of 150 Microsoft Entra custom role assignments for a single principal at any scope.</li><li>A maximum of 100 Microsoft Entra built-in role assignments for a single principal at non-tenant scope (such as an administrative unit or Microsoft Entra object). There is no limit to Microsoft Entra built-in role assignments at tenant scope. For more information, see [Assign Microsoft Entra roles at different scopes](../articles/active-directory/roles/assign-roles-different-scopes.md).</li><li>A group can't be added as a [group owner](../articles/active-directory/fundamentals/users-default-permissions.md?context=azure%2factive-directory%2fusers-groups-roles%2fcontext%2fugr-context#object-ownership).</li><li>A user's ability to read other users' tenant information can be restricted only by the Microsoft Entra organization-wide switch to disable all non-admin users' access to all tenant information (not recommended). For more information, see [To restrict the default permissions for member users](../articles/active-directory/fundamentals/users-default-permissions.md?context=azure%2factive-directory%2fusers-groups-roles%2fcontext%2fugr-context#restrict-member-users-default-permissions).</li><li>It might take up to 15 minutes or you might have to sign out and sign back in before admin role membership additions and revocations take effect.</li></ul> |
|Conditional Access Policies|A maximum of 195 policies can be created in a single Microsoft Entra organization (tenant).|
|Terms of use|You can add no more than 40 terms to a single Microsoft Entra organization (tenant).|
| Multitenant organizations | <ul><li>A maximum of 5 active tenants, including the owner tenant. The owner tenant can add more than 5 pending tenants, but they won't be able to join the multitenant organization if the limit is exceeded. This limit is applied at the time a pending tenant joins a multitenant organization.</li><li>A maximum of 100,000 internal users per active tenant. This limit is applied at the time a pending tenant joins a multitenant organization.</li></ul> |