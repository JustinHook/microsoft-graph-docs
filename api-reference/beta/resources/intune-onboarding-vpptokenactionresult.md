---
title: "vppTokenActionResult resource type"
description: "The status of the action performed with an Apple Volume Purchase Program token."
author: "tfitzmac"
---

# vppTokenActionResult resource type

> **Important:** APIs under the / beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

> **Note:** Using the Microsoft Graph APIs to configure Intune controls and policies still requires that the Intune service is [correctly licensed](https://go.microsoft.com/fwlink/?linkid=839381) by the customer.

The status of the action performed with an Apple Volume Purchase Program token.
## Properties
|Property|Type|Description|
|:---|:---|:---|
|actionName|String|Action name|
|actionState|[actionState](../resources/intune-shared-actionstate.md)|State of the action. Possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`.|
|startDateTime|DateTimeOffset|Time the action was initiated|
|lastUpdatedDateTime|DateTimeOffset|Time the action state was last updated|

## Relationships
None
## JSON Representation
Here is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.vppTokenActionResult"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.vppTokenActionResult",
  "actionName": "String",
  "actionState": "String",
  "startDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)"
}
```





