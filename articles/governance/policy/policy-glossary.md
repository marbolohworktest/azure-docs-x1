---
title: Azure Policy glossary
description: A glossary defining the terminology used throughout Azure Policy
ms.topic: conceptual
ms.date: 07/13/2022
---
# Azure Policy glossary

The term _policy_ is used widely in virtually every industry and is associated with many use cases. Azure Policy has specific vocabulary and applications that are not to be confused with policy embedded in other contexts.

This glossary provides definitions and descriptions of terms used by Azure Policy.

## Alias
A field used in policy definitions that maps to a resource property.
## Applicability
Describes the relevance of resources that are considered for assessment against a policy. A resource is considered applicable to a policy when it resides within the scope of the policy assignment, is not excluded or exempt from the policy assignment, and meets the conditions specified in the `if` block of the policy rule.
## Assignment
A JSON-defined object that determines the resources to which a policy definition is applied. Learn more about the policy assignment JSON structure here: [Azure Policy assignment structure](./concepts/assignment-structure.md).
## Azure Policy
A service that enables users to govern Azure resources by enforcing organizational standards and assessing compliance at scale.
## Built-in
Describes a type of policy definition that is available by default and generated by Azure Resource Providers. It is the alternative to a custom policy definition. View the list of available [built-in policy definitions](./samples/built-in-policies.md).
## Category
Metadata property in the policy definition that classifies the definition based on its area of focus. The category often indicates the resource provider of the target resource (For example: Compute, Storage, Monitoring).
## Compliance state
Describes a resource's adherence to applicable policies. Can be compliant, non-compliant, exempt, conflict, not started, or protected. Learn more about [how compliance works](./how-to/get-compliance-data.md).
## Compliant
A compliance state which indicates that a resource conformed to the policy rule in the policy definition.
## Control
Another term used for _group_, specifically in the context of regulatory compliance.
## Custom
Describes a type of policy definition that is authored by a policy user. It is the alternative to a built-in policy definition.
## Definition
A JSON-defined object that describes a policy, including resource compliance requirements and the effect to take if they are violated. Learn more about the policy definition JSON structure here: [Azure Policy definition structure](./concepts/definition-structure.md).
## Definition location
The scope to which an initiative definition or policy definition can be assigned. It can be either a management group or a subscription, and assignments can be made at or below that scope in the hierarchy.
## Effect
The action taken on a resource when the conditions of an applicable policy's rule are met. Learn more about [effects](./concepts/effects.md).
## Enforcement
Describes the preventative behavior that certain types of policy effects can have.
## Enforcement mode
A property of a policy assignment that allows users to enable or disable enforcement of certain policy effects like deny, while still evaluating for compliance and providing logs.
## Evaluation
Describes the process of scanning resources in the cloud environment to determine applicability and compliance of assigned policies.
## Event
An incident or outcome when something changes in Azure Policy, available for integration with Event Grid. Example events include instances in which a policy state is created, changed, or deleted. See [available event types for Azure Policy](../../event-grid/event-schema-policy.md).
## Exclusion
Also referred to as _NotScopes_; A property in the policy assignment which eliminates child resource containers or child resources from the assignment so they are not considered for compliance evaluation. Excluded scopes do not appear on the Azure portal Compliance blade. Learn more about [excluded scopes](./concepts/assignment-structure.md#excluded-scopes).
## Exempt
A compliance state which indicates that a resource is covered by an exemption.
## Exemption
A JSON-defined object that eliminates a resource hierarchy or an individual resource from evaluation. Resources that are exempt count toward overall compliance, but are not evaluated. Learn more about the exemption JSON structure here: [Azure Policy exemption structure](./concepts/exemption-structure.md).
## Group
A sub-collection of policy definition IDs within an initiative definition.
## Identity
A system-assigned or user-assigned managed identity used for remediation in Azure Policy. Learn more about [managed identities](../../active-directory/managed-identities-azure-resources/overview.md).
## Initiative
Also known as a _policy set_. A type of policy definition consisting of a collection of policy definition IDs. Used to centralize multiple policy definitions with a common goal that can share parameters, identities and be managed in a single assignment.
## JSON
Abbreviation for JavaScript Object Notation (JSON). Used by Azure Policy to define policy objects.
## Mode
Property on the policy definition that determines which resource types are evaluated for a policy definition. It is configured depending on whether the policy is targeting an Azure Resource Manager (ARM) property defined in an ARM template or a Resource Provider (RP) property.
## Non-compliant
A compliance state which indicates that a resource did not conform to the policy rule in the policy definition.
## Policy rule
The component of a policy definition that describes resource compliance requirements through logic-based conditional statements, as well as the effect taken if those conditions are not met. It is composed of an `if` block and `then` block.
## Policy state
Describes the aggregated compliance state of a policy assignment
## Regulatory Compliance
Describes a specific type of initiative that allows grouping of policies into controls and categorization of policies into compliance domains based on responsibility (_Customer_, _Microsoft_, _Shared_). There are many sample Regulatory Compliance built-ins, and customers have the ability to create their own. Learn more about [Regulatory Compliance](./concepts/regulatory-compliance.md).
> [!NOTE]
> Regulatory Compliance is a Preview feature.
## Remediation
A JSON-defined object that, when triggered, corrects resources violating policies with **deployIfNotExists** or **modify** effects. Remediation is only
automatic for resources during creation or update. Existing resources must be remediated by
triggering a remediation task. Learn how to [remediate non-compliant resources](./how-to/remediate-resources.md).
## Scope
The extent or area to which a policy is relevant, as described by Azure Resource Manager (ARM). It determines the set of resources that an assignment applies to, and may be a subscription, management group, resource group, or resource. Learn more about [scope in Azure Policy](./concepts/scope.md).
## Template info
The component of a policy definition used to define the constraint template. Specific to [Azure Policy for Kubernetes clusters](./concepts/policy-for-kubernetes.md).

## Next steps

To get started with Azure Policy, see [What is Azure Policy?](./overview.md).