---
title: "Create b2xUserFlow"
description: "Create a new b2xUserFlow object."
localization_priority: Normal
doc_type: apiPageType
author: "jkdouglas"
ms.prod: "microsoft-identity-platform"
---

# Create b2xUserFlow

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [b2xUserFlow](../resources/b2xuserflows.md) object.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account)|IdentityUserFlow.ReadWrite.All|
|Delegated (personal Microsoft account)| Not supported.|
|Application|IdentityUserFlow.ReadWrite.All|

The work or school account needs to belong to one of the following roles:

* Global administrator
* External Identity User Flow administrator

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
POST /identity/b2xUserFlow
```

## Request headers

|Name|Description|
|:---------------|:----------|
|Authorization|Bearer {token}. Required.|
|Content-Type|application/json. Required.|

## Request body

In the request body, provide a JSON representation of a [b2xUserFlow](../resources/b2xuserflows.md). All the properties listed in the following table are required.

|Property|Type|Description|
|:---------------|:--------|:----------|
|id|String|The name of the user flow. The name will be pre-pended with `B2X_1` after creation.|
|userFlowType|String|The type of user flow you are creating. This value will always be `signUpOrSignIn`.|
|userFlowTypeVersion|Float|The version of the user flow. This value will always be 1.|
|identityProviders|[IdentityProvider](../resources/identityprovider.md) collection|Optional. The identity providers you want to include in the user flow.|

## Response

If successful, this method returns a `201 Created` response code and a Location header with a URI to the [b2xUserFlow](../resources/b2xuserflows.md) object created for this request, with the `B2X_1` prefix added to the name. If unsuccessful, a `4xx` error will be returned with specific details.

## Examples

### Example 1: Create a user flow with the default values

#### Request

The following is an example of the request.

<!-- {
  "blockType": "request",
  "name": "create_b2xuserflow_from_b2xuserflows"
}
-->

``` http
POST https://graph.microsoft.com/beta/identity/b2xUserFlows
Content-type: application/json
Content-length: 154

{
    "id": "Partner",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1
}
```

#### Response

The following is an example of the response.

**Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.b2xIdentityUserFlow"
} -->

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/beta/identity/b2xUserFlows/B2X_1_Partner
Content-type: application/json

{
    "id": "B2X_1_Partner",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1
}
```

### Example 2: Create a user flow with the default values and an identity provider

#### Request

The following is an example of the request.

<!-- {
  "blockType": "request",
  "name": "create_b2xuserflow_from_b2xuserflows_identityProviders"
}
-->

``` http
POST https://graph.microsoft.com/beta/identity/b2xUserFlows
Content-type: application/json
Content-length: 154

{
    "id": "Partner",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1,
    "identityProviders": [
        {
            "id": "Facebook-OAuth",
            "type": "Facebook",
            "name": "Facebook"
        }
    ]
}
```

#### Response

The following is an example of the response.

**Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.b2xIdentityUserFlow"
} -->

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/beta/identity/b2xUserFlows/B2X_1_Partner
Content-type: application/json

{
    "id": "B2X_1_Partner",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1
}
```