---
title: Troubleshoot Azure Operator Nexus server problems
description: Troubleshoot cluster bare metal machines with Restart, Reimage, Replace for Azure Operator Nexus.
ms.service: azure-operator-nexus
ms.custom: troubleshooting
ms.topic: troubleshooting
ms.date: 04/24/2024
author: eak13
ms.author: ekarandjeff
---

# Troubleshoot Azure Operator Nexus server problems

This article describes how to troubleshoot server problems by using restart, reimage, and replace actions on Azure Operator Nexus bare metal machines (BMMs). You might need to take these actions on your server for maintenance reasons, which causes a brief disruption to specific BMMs.

The time required to complete each of these actions is similar. Restarting is the fastest, whereas replacing takes slightly longer. All three actions are simple and efficient methods for troubleshooting.

> [!CAUTION]
> Do not perform any action against management servers without first consulting with Microsoft support personnel. Doing so could affect the integrity of the Operator Nexus Cluster.

## Prerequisites

- Familiarize yourself with the capabilities referenced in this article by reviewing the [BMM actions](howto-baremetal-functions.md).
- Gather the following information:
  - Name of the resource group for the BMM
  - Name of the BMM that requires a lifecycle management operation

> [!IMPORTANT]
> Disruptive command requests against a Kubernetes Control Plane (KCP) node are rejected if there is another disruptive action command already running against another KCP node or if the full KCP is not available.
>
> Restart, reimage and replace are all considered disruptive actions.
>
> This check is done to maintain the integrity of the Nexus instance and ensure multiple KCP nodes don't go down at once due to simultaneous disruptive actions. If multiple nodes go down, it will break the healthy quorum threshold of the Kubernetes Control Plane.

## Identify the corrective action

When you're troubleshooting a BMM for failures and determining the best corrective action, it's important to understand the available options. Restarting or reimaging a BMM can be an efficient and effective way to fix problems or restore the software to a known-good place. Replacing a BMM might be required when one or more hardware components fail on the server. This article provides direction on the best practices for each of the three actions.

Troubleshooting technical problems requires a systematic approach. One effective method is to start with the least invasive solution and works your way up to more complex and drastic measures, if necessary.

The first step in troubleshooting is often to try restarting the device or system. Restarting can help to clear any temporary glitches or errors that might be causing the problem. If restarting doesn't solve the problem, the next step might be to try reimaging the device or system.

If reimaging doesn't solve the problem, the final step might be to replace the faulty hardware component. Replacement can be a more drastic measure, but it might be necessary if the problem is related to a hardware malfunction.

Keep in mind that these troubleshooting methods might not always be effective, and other factors in play might require a different approach.

## Troubleshoot with a restart action

Restarting a BMM is a process of restarting the server through a simple API call. This action can be useful for troubleshooting problems when tenant virtual machines on the host aren't responsive or are otherwise stuck.

The restart typically is the starting point for mitigating a problem.

## Troubleshoot with a reimage action

Reimaging a BMM is a process that you use to redeploy the image on the OS disk, without affecting the tenant data. This action executes the steps to rejoin the cluster with the same identifiers.

The reimage action can be useful for troubleshooting problems by restoring the OS to a known-good working state. Common causes that can be resolved through reimaging include recovery due to doubt of host integrity, suspected or confirmed security compromise, or "break glass" write activity.

A reimage action is the best practice for lowest operational risk to ensure the integrity of the BMM.

## Troubleshoot with a replace action

Servers contain many physical components that can fail over time. It's important to understand which physical repairs require BMM replacement and when BMM replacement is recommended but not required.

A hardware validation process is invoked to ensure the integrity of the physical host in advance of deploying the OS image. Like the reimage action, the tenant data isn't modified during replacement.

> [!IMPORTANT]
> Starting with the 2024-07-01 GA API version, the RAID controller is reset during BMM replace, wiping all data from the server's virtual disks. Baseboard Management Controller (BMC) virtual disk alerts triggered during BMM replace can be ignored unless there are additonal physical disk and/or RAID controllers alerts.

As a best practice, first issue a `cordon` command to remove the bare metal machine from workload scheduling and then shut down the BMM in advance of physical repairs.

When you're performing a physical hot swappable power supply repair, a replace action isn't required because the BMM host will continue to function normally after the repair.

When you're performing the following physical repairs, we recommend a replace action, though it isn't necessary to bring the BMM back into service:

- CPU
- Dual In-Line Memory Module (DIMM)
- Fan
- Expansion board riser
- Transceiver
- Ethernet or fiber cable replacement

When you're performing the following physical repairs, a replace action is required to bring the BMM back into service:

- Backplane
- System board
- SSD disk
- PERC/RAID adapter
- Mellanox Network Interface Card (NIC)
- Broadcom embedded NIC

## Summary

Restarting, reimaging, and replacing are effective troubleshooting methods that you can use to address technical problems. However, it's important to have a systematic approach and to consider other factors before you try any drastic measures.
More details about the BMM actions can be found in the [BMM actions](howto-baremetal-functions.md) article.

If you still have questions, [contact support](https://portal.azure.com/?#blade/Microsoft_Azure_Support/HelpAndSupportBlade).
For more information about Support plans, see [Azure Support plans](https://azure.microsoft.com/support/plans/response/).
