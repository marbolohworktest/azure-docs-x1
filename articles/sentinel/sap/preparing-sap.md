---
title: Configure your SAP system for the Microsoft Sentinel solution
titleSuffix: Microsoft Sentinel
description: Learn about extra preparations required in your SAP system to install the SAP data connector agent and connect Microsoft Sentinel to your SAP system.
author: batamig
ms.author: bagol
ms.topic: how-to
ms.date: 09/16/2024
appliesto:
    - Microsoft Sentinel in the Azure portal
    - Microsoft Sentinel in the Microsoft Defender portal
ms.collection: usx-security
#Customer intent: As an SAP BASIS team member, I want to configure SAP authorizations and deploy optional SAP Change Requests so that I can ensure proper connectivity and log retrieval from SAP systems for security monitoring.

---

# Configure your SAP system for the Microsoft Sentinel solution

This article describes how to prepare your SAP environment for connecting to the SAP data connector agent. Preparation includes configuring required SAP authorizations and, optionally, deploying extra SAP change requests (CRs).

This article is part of the second step in deploying the Microsoft Sentinel solution for SAP applications.

:::image type="content" source="media/deployment-steps/prepare-sap-environment.png" alt-text="Diagram of the deployment flow for the Microsoft Sentinel solution for SAP applications, with the preparing SAP step highlighted." border="false":::

The procedures in this article are typically performed by your **SAP BASIS** team.

## Prerequisites

- Before you start, make sure to review the [prerequisites for deploying the Microsoft Sentinel solution for SAP applications](prerequisites-for-deploying-sap-continuous-threat-monitoring.md).

## Configure the Microsoft Sentinel role

To allow the SAP data connector to connect to your SAP system, you must create an SAP system role specifically for this purpose. 

- **To include both log retrieval and [attack disruption response actions](https://aka.ms/attack-disrupt-defender)**, we recommend creating this role by loading role authorizations from the [**/MSFTSEN/SENTINEL_RESPONDER**](https://aka.ms/SAP_Sentinel_Responder_Role) file.

- **To include log retrieval only**, we recommend creating this role by deploying the *NPLK900271* SAP change request (CR): [K900271.NPL](https://raw.githubusercontent.com/Azure/Azure-Sentinel/master/Solutions/SAP/CR/K900271.NPL) | [R900271.NPL](https://raw.githubusercontent.com/Azure/Azure-Sentinel/master/Solutions/SAP/CR/R900271.NPL)

    Deploy the CRs on your SAP system as needed just as you'd deploy other CRs. We strongly recommend that deploying SAP CRs is done by an experienced SAP system administrator. For more information, see the [SAP documentation](https://help.sap.com/docs/ABAP_PLATFORM_NEW/4a368c163b08418890a406d413933ba7/e15d9acae75c11d2b451006094b9ea64.html?locale=en-US&version=LATEST).

    Alternately, load the role authorizations from the [**MSFTSEN_SENTINEL_CONNECTOR**](https://aka.ms/SAP_Sentinel_Connector_Role) file, which includes all the basic permissions for the data connector to operate.

    Experienced SAP administrators might choose to create the role manually and assign it the appropriate permissions. In such cases, create a role manually with the relevant authorizations required for the logs you want to ingest. For more information, see [Required ABAP authorizations](required-abap-authorizations.md). Examples in our documentation use the **/MSFTSEN/SENTINEL_RESPONDER** name.

When configuring the role, we recommend that you:

- Generate an active role profile for Microsoft Sentinel by running the **PFCG** transaction.
- Use `/MSFTSEN/SENTINEL_RESPONDER` as the role name.

 For more information, see the [SAP documentation](https://help.sap.com/doc/saphelp_nw73ehp1/7.31.19/en-US/48/e8eb38f94cb138e10000000a114084/frameset.htm) on creating roles.

### Create a user

The Microsoft Sentinel solution for SAP applications requires a user account to connect to your SAP system. When creating your user:

- Make sure to create a system user.
- Assign the **/MSFTSEN/SENTINEL_RESPONDER** role to the user, which you'd created in the [previous step](#configure-the-microsoft-sentinel-role).

For more information, see the [SAP documentation](https://help.sap.com/docs/ABAP_PLATFORM_NEW/ad77b44570314f6d8c3a8a807273084c/4cb5f7ac9cb33c94e10000000a42189c.html?version=LATEST).

## Configure SAP auditing

Some installations of SAP systems might not have audit logging enabled by default. For best results in evaluating the performance and efficacy of the Microsoft Sentinel solution for SAP applications, enable auditing of your SAP system and configure the audit parameters. If you want to ingest SAP HANA DB logs, make sure to also enable auditing for SAP HANA DB.

We recommend that you configure auditing for all messages from the audit log, as this data is useful for Microsoft Sentinel detections and in post-compromise investigations and hunting.

For more information, see the [SAP community](https://community.sap.com/t5/application-development-blog-posts/analysis-and-recommended-settings-of-the-security-audit-log-sm19-rsau/ba-p/13297094) and [Collect SAP HANA audit logs in Microsoft Sentinel](collect-sap-hana-audit-logs.md).

## Configure support for extra data retrieval (recommended)

While this step is optional, we recommend that you deploy extra CRs from the [Microsoft Sentinel GitHub repository](https://github.com/Azure/Azure-Sentinel/tree/master/Solutions/SAP/CR) to enable the SAP data connector to retrieve the following content information from your SAP system:

- **DB Table** and **Spool Output** logs
- **Client IP address information** from the security audit logs (SAP BASIS version 7.5 SP12 and higher only)

Deploy the relevant CRs according to your SAP version:

| SAP BASIS versions | Recommended CR |
| --- | --- | --- |
| **750 and higher** | *NPLK900202*: [K900202.NPL](https://raw.githubusercontent.com/Azure/Azure-Sentinel/master/Solutions/SAP/CR/K900202.NPL), [R900202.NPL](https://raw.githubusercontent.com/Azure/Azure-Sentinel/master/Solutions/SAP/CR/R900202.NPL) <br><br>When deploying this CR any of the following SAP versions, also deploy [2641084 - Standardized read access to data of Security Audit Log](https://launchpad.support.sap.com/#/notes/2641084): <br>- 750 SP04 to SP12<br>- 751 SP00 to SP06<br>- 752 SP00 to SP02  | 
| **740**  | *NPLK900201*: [K900201.NPL](https://raw.githubusercontent.com/Azure/Azure-Sentinel/master/Solutions/SAP/CR/K900201.NPL), [R900201.NPL](https://raw.githubusercontent.com/Azure/Azure-Sentinel/master/Solutions/SAP/CR/R900201.NPL) |

Deploy the CRs on your SAP system as needed just as you'd deploy other CRs. We strongly recommend that deploying SAP CRs is done by an experienced SAP system administrator. For more information, see the [SAP documentation](https://help.sap.com/docs/ABAP_PLATFORM_NEW/4a368c163b08418890a406d413933ba7/e15d9acae75c11d2b451006094b9ea64.html?locale=en-US&version=LATEST).

For more information, see the [SAP Community](https://community.sap.com/t5/application-development-blog-posts/analysis-and-recommended-settings-of-the-security-audit-log-sm19-rsau/ba-p/13297094) and the [SAP documentation](https://help.sap.com/docs/ABAP_PLATFORM_NEW/4a368c163b08418890a406d413933ba7/e15d9acae75c11d2b451006094b9ea64.html?locale=en-US&version=LATEST).

## Verify that the PAHI table is updated at regular intervals

The SAP PAHI table includes data on the history of the SAP system, the database, and SAP parameters. In some cases, the Microsoft Sentinel solution for SAP applications can't monitor the SAP PAHI table at regular intervals, due to missing or faulty configuration. It's important to update the PAHI table and to monitor it frequently, so that the Microsoft Sentinel solution for SAP applications can alert on suspicious actions that might happen at any time throughout the day. For more information, see:

- [SAP note 12103](https://launchpad.support.sap.com/#/notes/12103)
- [Monitoring the configuration of static SAP security parameters (Preview)](sap-solution-security-content.md#monitor-the-configuration-of-static-sap-security-parameters-preview)

If the PAHI table is updated regularly, the `SAP_COLLECTOR_FOR_PERFMONITOR` job is scheduled and runs hourly. If the `SAP_COLLECTOR_FOR_PERFMONITOR` job doesn't exist, make sure to configure it as needed. 

For more information, see [Database Collector in Background Processing](https://help.sap.com/doc/saphelp_nw75/7.5.5/c4/3a735b505211d189550000e829fbbd/frameset.htm) and [Configuring the Data Collector](https://help.sap.com/docs/SAP_NETWEAVER_AS_ABAP_752/3364beced9d145a5ad185c89a1e04658/c43a818c505211d189550000e829fbbd.html).

## Configure your system to use SNC for secure connections

By default, the SAP data connector agent connects to an SAP server using a remote function call (RFC) connection and a username and password for authentication.

However, you might need to make the connection on an encrypted channel or use client certificates for authentication. In these cases, use Smart Network Communications (SNC) from SAP to secure your data connections, as described in this section.

In a production environment, we strongly recommend that your consult with SAP administrators to create a deployment plan for configuring SNC. For more information, see the [SAP documentation](https://help.sap.com/docs/ABAP_PLATFORM_NEW/e73bba71770e4c0ca5fb2a3c17e8e229/e656f466e99a11d1a5b00000e835363f.html). 

When configuring SNC:

- If the client certificate was issued by an enterprise certification authority, transfer the issuing CA and root CA certificates to the system where you plan to create the data connector agent.
- Make sure to also enter the relevant values and use the relevant procedures when [configuring the SAP data connector agent container](deploy-data-connector-agent-container.md).



## Next step

> [!div class="nextstepaction"]
> [Connect your SAP system by deploying your data connector agent container](deploy-data-connector-agent-container.md)
