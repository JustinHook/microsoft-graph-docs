---
title: "mobileAppCategory resource type"
description: "Contains properties for a single Intune app category."
author: "tfitzmac"
---

# mobileAppCategory resource type

> **Important:** APIs under the / beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

> **Note:** Using the Microsoft Graph APIs to configure Intune controls and policies still requires that the Intune service is [correctly licensed](https://go.microsoft.com/fwlink/?linkid=839381) by the customer.

Contains properties for a single Intune app category.
## Methods
|Method|Return Type|Description|
|:---|:---|:---|
|[List mobileAppCategories](../api/intune-apps-mobileappcategory-list.md)|[mobileAppCategory](../resources/intune-apps-mobileappcategory.md) collection|List properties and relationships of the [mobileAppCategory](../resources/intune-apps-mobileappcategory.md) objects.|
|[Get mobileAppCategory](../api/intune-apps-mobileappcategory-get.md)|[mobileAppCategory](../resources/intune-apps-mobileappcategory.md)|Read properties and relationships of the [mobileAppCategory](../resources/intune-apps-mobileappcategory.md) object.|
|[Create mobileAppCategory](../api/intune-apps-mobileappcategory-create.md)|[mobileAppCategory](../resources/intune-apps-mobileappcategory.md)|Create a new [mobileAppCategory](../resources/intune-apps-mobileappcategory.md) object.|
|[Delete mobileAppCategory](../api/intune-apps-mobileappcategory-delete.md)|None|Deletes a [mobileAppCategory](../resources/intune-apps-mobileappcategory.md).|
|[Update mobileAppCategory](../api/intune-apps-mobileappcategory-update.md)|[mobileAppCategory](../resources/intune-apps-mobileappcategory.md)|Update the properties of a [mobileAppCategory](../resources/intune-apps-mobileappcategory.md) object.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|id|String|The key of the entity.|
|displayName|String|The name of the app category.|
|lastModifiedDateTime|DateTimeOffset|The date and time the mobileAppCategory was last modified.|

## Relationships
None
## JSON Representation
Here is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.mobileAppCategory"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.mobileAppCategory",
  "id": "String (identifier)",
  "displayName": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```





