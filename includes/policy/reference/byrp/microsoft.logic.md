---
ms.service: azure-policy
ms.topic: include
ms.date: 11/04/2024
ms.author: davidsmatlak
author: davidsmatlak
ms.custom: generated
---

|Name<br /><sub>(Azure portal)</sub> |Description |Effect(s) |Version<br /><sub>(GitHub)</sub> |
|---|---|---|---|
|[Deploy Diagnostic Settings for Logic Apps to Event Hub](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fa1dae6c7-13f3-48ea-a149-ff8442661f60) |Deploys the diagnostic settings for Logic Apps to stream to a regional Event Hub when any Logic Apps which is missing this diagnostic settings is created or updated. |DeployIfNotExists, Disabled |[2.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/LogicApps_DeployDiagnosticLog_Deploy_EventHub.json) |
|[Deploy Diagnostic Settings for Logic Apps to Log Analytics workspace](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fb889a06c-ec72-4b03-910a-cb169ee18721) |Deploys the diagnostic settings for Logic Apps to stream to a regional Log Analytics workspace when any Logic Apps which is missing this diagnostic settings is created or updated. |DeployIfNotExists, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/LogicApps_DeployDiagnosticLog_Deploy_LogAnalytics.json) |
|[Enable logging by category group for Integration accounts (microsoft.logic/integrationaccounts) to Event Hub](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fda9b245a-05a9-4c2a-acb3-5afe62658776) |Resource logs should be enabled to track activities and events that take place on your resources and give you visibility and insights into any changes that occur. This policy deploys a diagnostic setting using a category group to route logs to an Event Hub for Integration accounts (microsoft.logic/integrationaccounts). |DeployIfNotExists, AuditIfNotExists, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/DS_EH_logic-integrationaccounts_DINE.json) |
|[Enable logging by category group for Integration accounts (microsoft.logic/integrationaccounts) to Log Analytics](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F1840aef8-71df-4a30-a108-efdb4f291a7f) |Resource logs should be enabled to track activities and events that take place on your resources and give you visibility and insights into any changes that occur. This policy deploys a diagnostic setting using a category group to route logs to a Log Analytics workspace for Integration accounts (microsoft.logic/integrationaccounts). |DeployIfNotExists, AuditIfNotExists, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/DS_LA_logic-integrationaccounts_DINE.json) |
|[Enable logging by category group for Integration accounts (microsoft.logic/integrationaccounts) to Storage](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F8464ded4-af15-4319-950f-a30400d35247) |Resource logs should be enabled to track activities and events that take place on your resources and give you visibility and insights into any changes that occur. This policy deploys a diagnostic setting using a category group to route logs to a Storage Account for Integration accounts (microsoft.logic/integrationaccounts). |DeployIfNotExists, AuditIfNotExists, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/DS_ST_logic-integrationaccounts_DINE.json) |
|[Enable logging by category group for Logic apps (microsoft.logic/workflows) to Event Hub](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F58e22268-dacf-4b7f-b445-338a7e56d23c) |Resource logs should be enabled to track activities and events that take place on your resources and give you visibility and insights into any changes that occur. This policy deploys a diagnostic setting using a category group to route logs to an Event Hub for Logic apps (microsoft.logic/workflows). |DeployIfNotExists, AuditIfNotExists, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/DS_EH_logic-workflows_DINE.json) |
|[Enable logging by category group for Logic apps (microsoft.logic/workflows) to Log Analytics](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F63d1a629-735c-448b-b45f-5e3865e84cf5) |Resource logs should be enabled to track activities and events that take place on your resources and give you visibility and insights into any changes that occur. This policy deploys a diagnostic setting using a category group to route logs to a Log Analytics workspace for Logic apps (microsoft.logic/workflows). |DeployIfNotExists, AuditIfNotExists, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/DS_LA_logic-workflows_DINE.json) |
|[Enable logging by category group for Logic apps (microsoft.logic/workflows) to Storage](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Ff9431f54-4c78-47ef-aac9-2b37cbaeae75) |Resource logs should be enabled to track activities and events that take place on your resources and give you visibility and insights into any changes that occur. This policy deploys a diagnostic setting using a category group to route logs to a Storage Account for Logic apps (microsoft.logic/workflows). |DeployIfNotExists, AuditIfNotExists, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/DS_ST_logic-workflows_DINE.json) |
|[Logic Apps Integration Service Environment should be encrypted with customer-managed keys](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F1fafeaf6-7927-4059-a50a-8eb2a7a6f2b5) |Deploy into Integration Service Environment to manage encryption at rest of Logic Apps data using customer-managed keys. By default, customer data is encrypted with service-managed keys, but customer-managed keys are commonly required to meet regulatory compliance standards. Customer-managed keys enable the data to be encrypted with an Azure Key Vault key created and owned by you. You have full control and responsibility for the key lifecycle, including rotation and management. |Audit, Deny, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Logic%20Apps/ISEWithCustomerManagedKey_AuditDeny.json) |
|[Logic Apps should be deployed into Integration Service Environment](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fdc595cb1-1cde-45f6-8faf-f88874e1c0e1) |Deploying Logic Apps into Integration Service Environment in a virtual network unlocks advanced Logic Apps networking and security features and provides you with greater control over your network configuration. Learn more at: [https://aka.ms/integration-service-environment](https://aka.ms/integration-service-environment). Deploying into Integration Service Environment also allows encryption with customer-managed keys which provides enhanced data protection by allowing you to manage your encryption keys. This is often to meet compliance requirements. |Audit, Deny, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Logic%20Apps/LogicAppsInISE_AuditDeny.json) |
|[Resource logs in Logic Apps should be enabled](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F34f95f76-5386-4de7-b824-0d8478470c9d) |Audit enabling of resource logs. This enables you to recreate activity trails to use for investigation purposes; when a security incident occurs or when your network is compromised |AuditIfNotExists, Disabled |[5.1.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Logic%20Apps/AuditDiagnosticLog_Audit.json) |