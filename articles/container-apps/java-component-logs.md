---
title: Observability of managed Java components in Azure Container Apps
description: Learn how to retrieve logs of managed Java components in Azure Container Apps.
services: container-apps
author: craigshoemaker
ms.service: azure-container-apps
ms.custom: devx-track-extended-java, devx-track-azurecli
ms.topic: how-to
ms.date: 05/01/2024
ms.author: cshoe
zone_pivot_groups: container-apps-portal-or-cli
---

# Tutorial: Observability of managed Java components in Azure Container Apps

Java components include built-in observability features that can give you a holistic view of Java component health throughout its lifecycle. In this tutorial, you learn how to query logs messages generated by a Java component.

## Prerequisites

The following prerequisites are required for this tutorial.

| Resource | Description |
|---|---|
| Azure Log Analytics | To use the built-in observability features of managed Java components, ensure you set up Azure Log Analytics to use Log Analytics or *Azure Monitor*. For more information, see [Log storage and monitoring options in Azure Container Apps](log-options.md). |
| Java component | Make sure to create at least one Java component in your environment, such as [Eureka Server](java-eureka-server.md) or [Config Server](java-config-server.md). |

## Query log data

Log Analytics is a tool that helps you view and analyze log data. Using Log Analytics, you can write Kusto queries to retrieve, sort, filter, and visualize log data. These visualizations help you spot trends and identify issues with your application. You can work interactively with the query results or use them with other features such as alerts, dashboards, and workbooks.

::: zone pivot="azure-portal"

1. Open the Azure portal and go to your Azure Log Analytics workspace.

1. Select **Logs** from the sidebar.

1. In the query tab, under the *Tables* section, under *Custom Logs*, select the **ContainerAppSystemlogs_CL** table.

1. Enter the following Kusto query to display Eureka Server logs for the Spring component.

    ```kusto
    ContainerAppSystemLogs_CL
    | where ComponentType_s == 'SpringCloudEureka'
    | project Time=TimeGenerated, Type=ComponentType_s, Component=ComponentName_s, Message=Log_s
    | take 100
    ```

    :::image type="content" source="media/java-components-logs/java-component-logs.png" alt-text="Screenshot of the Log Analytics Java component logs."  lightbox="media/java-components-logs/java-component-logs.png":::

1. Select the **Run** button to run the query.

::: zone-end

::: zone pivot="azure-cli"

You query the component logs via the Azure CLI [log analytics](/cli/azure/monitor/log-analytics) extension.

1. Run the following command to create a variable for your Log Analytics workspace ID.

    Make sure to replace `<WORKSPACE_ID>` with your Log Analytics workspace ID before running the query.

    # [Bash](#tab/bash)

    ```azurecli
    SET $WORKSPACE_ID=<WORKSPACE_ID>
    ```

    # [PowerShell](#tab/powershell)

    ```powershell
    $WORKSPACE_ID = "<WORKSPACE_ID>"
    ```

    ---

1. Run the following command to query the logs table.

    # [Bash](#tab/bash)

    ```azurecli
    az monitor log-analytics query \
      --workspace $WORKSPACE_ID \
      --analytics-query "ContainerAppSystemLogs_CL | where ComponentType_s == 'SpringCloudEureka' | project Time=TimeGenerated, Type=ComponentType_s, Component=ComponentName_s, Message=Log_s | take 5" --out table
    ```

    # [PowerShell](#tab/powershell)

    ```powershell
    $queryResults = Invoke-AzOperationalInsightsQuery -WorkspaceId $WORKSPACE_ID -Query "ContainerAppSystemLogs_CL | where ComponentType_s == 'SpringCloudEureka' | project Time=TimeGenerated, Type=ComponentType_s, Component=ComponentName_s, Message=Log_s | take 5"
    $queryResults.Results
    ```

    ---

    The `project` operator's parameters specify the table columns.

::: zone-end

## Query Java Component Log with Azure monitor

You can query Azure Monitor for monitoring data for your Java component logs.

::: zone pivot="azure-portal"

1. Open the Azure portal and go to your Container Apps environment.

1. From the sidebar, under the *Monitoring* section, select **Logs**.

1. In the query tab, in the *Tables* section, under the *Container Apps* heading, select the **ContainerAppSystemLogs** table.

1. Enter the following Kusto query to display the log entries of Eureka Server for Spring component logs.

    ```kusto
    ContainerAppSystemLogs
    | where ComponentType == "SpringCloudEureka"
    | project Time=TimeGenerated, Type=ComponentType, Component=ComponentName, Message=Log
    | take 100
    ```

1. Select the **Run** button to run the query.

::: zone-end

::: zone pivot="azure-cli"

You query the component logs via the Azure CLI [log analytics](/cli/azure/monitor/log-analytics) extension.

1. Run the following command to create a variable for your Log Analytics workspace ID.

    Make sure to replace `<WORKSPACE_ID>` with your Log Analytics workspace ID before running the query.

    # [Bash](#tab/bash)

    ```azurecli
    SET $WORKSPACE_ID=<WORKSPACE_ID>
    ```

    # [PowerShell](#tab/powershell)

    ```powershell
    $WORKSPACE_ID = "<WORKSPACE_ID>"
    ```

    ---

1. Run the following command to query the logs table.

    # [Bash](#tab/bash)

    ```azurecli
    az monitor log-analytics query --workspace $WORKSPACE_CUSTOMER_ID --analytics-query "ContainerAppSystemLogs | where ComponentType == 'SpringCloudEureka' | project Time=TimeGenerated, Type=ComponentType, Component=ComponentName, Message=Log | take 5" --out table
    ```

    # [PowerShell](#tab/powershell)

    ```powershell
    $queryResults = Invoke-AzOperationalInsightsQuery -WorkspaceId $WORKSPACE_ID -Query "ContainerAppSystemLogs | where ComponentType == 'SpringCloudEureka' | project Time=TimeGenerated, Type=ComponentType, Component=ComponentName, Message=Log | take 5"
    $queryResults.Results
    ```

    ---

    The `project` operator's parameters specify the table columns.

::: zone-end

## Next steps

> [!div class="nextstepaction"]
> [Log storage and monitoring options in Azure Container Apps](log-options.md)