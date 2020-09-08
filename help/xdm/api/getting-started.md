---
keywords: Experience Platform;home;popular topics;api;API;XDM;XDM system;;experience data model;Experience data model;Experience Data Model;data model;Data Model;schema registry;Schema Registry;
solution: Experience Platform
title: Schema Registry API developer guide
description: The Schema Registry is used to access the Schema Library within Adobe Experience Platform, providing a user interface and RESTful API from which all available library resources are accessible. Using the Schema Registry API, you can perform basic CRUD operations in order to view and manage all schemas and related resources available to you within Adobe Experience Platform.
topic: developer guide
---

# [!DNL Schema Registry] API developer guide

The [!DNL Schema Registry] is used to access the Schema Library within Adobe Experience Platform, providing a user interface and RESTful API from which all available library resources are accessible.

Using the Schema Registry API, you can perform basic CRUD operations in order to view and manage all schemas and related resources available to you within Adobe Experience Platform. This includes those defined by Adobe, [!DNL Experience Platform] partners, and vendors whose applications you use. You can also use API calls to create new schemas and resources for your organization, as well as view and edit resources that you have already defined.

This developer guide provides steps to help you start using the [!DNL Schema Registry] API. The guide then provides sample API calls for performing key operations using the [!DNL Schema Registry].

## Prerequisites

This guide requires a working understanding of the following components of Adobe Experience Platform:

* [[!DNL Experience Data Model (XDM) System]](../home.md): The standardized framework by which [!DNL Experience Platform] organizes customer experience data.
    * [Basics of schema composition](../schema/composition.md): Learn about the basic building blocks of XDM schemas.
* [[!DNL Real-time Customer Profile]](../../profile/home.md): Provides a unified, real-time consumer profile based on aggregated data from multiple sources.
* [[!DNL Sandboxes]](../../sandboxes/home.md): [!DNL Experience Platform] provides virtual sandboxes which partition a single [!DNL Platform] instance into separate virtual environments to help develop and evolve digital experience applications.

The following sections provide additional information that you will need to know in order to successfully make calls to the [!DNL Schema Registry] API.

## Reading sample API calls

This guide provides example API calls to demonstrate how to format your requests. These include paths, required headers, and properly formatted request payloads. Sample JSON returned in API responses is also provided. For information on the conventions used in documentation for sample API calls, see the section on [how to read example API calls](../../landing/troubleshooting.md#how-do-i-format-an-api-request) in the [!DNL Experience Platform] troubleshooting guide.

## Gather values for required headers

In order to make calls to [!DNL Platform] APIs, you must first complete the [authentication tutorial](../../tutorials/authentication.md). Completing the authentication tutorial provides the values for each of the required headers in all [!DNL Experience Platform] API calls, as shown below:

* Authorization: Bearer `{ACCESS_TOKEN}`
* x-api-key: `{API_KEY}`
* x-gw-ims-org-id: `{IMS_ORG}`

All resources in [!DNL Experience Platform], including those belonging to the [!DNL Schema Registry], are isolated to specific virtual sandboxes. All requests to [!DNL Platform] APIs require a header that specifies the name of the sandbox the operation will take place in:

* x-sandbox-name: `{SANDBOX_NAME}`

>[!NOTE]
>
>For more information on sandboxes in [!DNL Platform], see the [sandbox overview documentation](../../sandboxes/home.md). 

All lookup (GET) requests to the [!DNL Schema Registry] require an additional Accept header, whose value determines the format of information returned by the API. See the [Accept header](#accept) section below for more details.

All requests that contain a payload (POST, PUT, PATCH) require an additional header:

* Content-Type: application/json

## Know your TENANT_ID {#know-your-tenant_id}

Throughout this guide you will see references to a `TENANT_ID`. This ID is used to ensure that resources you create are namespaced properly and contained within your IMS Organization. If you do not know your ID, you can access it by performing the following GET request:

**API format**

```http
GET /stats
```

**Request**

```SHELL
curl -X GET \
  https://platform.adobe.io/data/foundation/schemaregistry/stats \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'x-sandbox-name: {SANDBOX_NAME}'
```

**Response**

A successful response returns information regarding your organization's use of the [!DNL Schema Registry]. This includes a `tenantId` attribute, the value of which is your `TENANT_ID`. 

```JSON
{
  "imsOrg":"{IMS_ORG}",
  "tenantId":"{TENANT_ID}",
  "counts": {
    "schemas": 4,
    "mixins": 3,
    "datatypes": 1,
    "classes": 2,
    "unions": 0,
  },
  "recentlyCreatedResources": [ 
    {
      "title": "Sample Mixin",
      "description": "New Sample Mixin.",
      "meta:resourceType": "mixins",
      "meta:created": "Sat Feb 02 2019 00:24:30 GMT+0000 (UTC)",
      "version": "1.1"
    },
    {
      "$id": "https://ns.adobe.com/{TENANT_ID}/classes/5bdb5582be0c0f3ebfc1c603b705764f",
      "title": "Tenant Class",
      "description": "Tenant Defined Class",
      "meta:resourceType": "classes",
      "meta:created": "Fri Feb 01 2019 22:46:21 GMT+0000 (UTC)",
      "version": "1.0"
    } 
  ],
  "recentlyUpdatedResources": [
    {
      "title": "Sample Mixin",
      "description": "New Sample Mixin.",
      "meta:resourceType": "mixins",
      "meta:updated": "Sat Feb 02 2019 00:34:06 GMT+0000 (UTC)",
      "version": "1.1"
    },
    {
      "title": "Data Schema",
      "description": "Schema for Data Information",
      "meta:resourceType": "schemas",
      "meta:updated": "Fri Feb 01 2019 23:47:43 GMT+0000 (UTC)",
      "meta:class": "https://ns.adobe.com/{TENANT_ID}/classes/47b2189fc135e03c844b4f25139d10ab",
      "meta:classTitle": "Sample Class",
      "version": "1.1"
    }
 ],
 "classUsage": {
    "https://ns.adobe.com/{TENANT_ID}/classes/47b2189fc135e03c844b4f25139d10ab": [
      {
        "$id": "https://ns.adobe.com/{TENANT_ID}/schemas/274f17bc5807ff307a046bab1489fb18",
        "title": "Tenant Data Schema",
        "description": "Schema for tenant-specific data."
      }
    ],
    "https://ns.adobe.com/xdm/context/profile": [
      {
        "$id": "https://ns.adobe.com/{TENANT_ID}/schemas/3ac6499f0a43618bba6b138226ae3542",
        "title": "Simple Profile",
        "description": "A simple profile schema."
      },
      {
        "$id": "https://ns.adobe.com/{TENANT_ID}/schemas/fbc52b243d04b5d4f41eaa72a8ba58be",
        "title": "Program Schema",
        "description": "Schema for program-related data."
      },
      {
        "$id": "https://ns.adobe.com/{TENANT_ID}/schemas/4025a705890c6d4a4a06b16f8cf6f4ca",
        "title": "Sample Schema",
        "description": "A sample schema."
      }
    ]
  }
 }
```

* `tenantId`: The `TENANT_ID` value for your IMS Organization.

## Understand the `CONTAINER_ID` {#container}

Calls to the [!DNL Schema Registry] API require the use of a `CONTAINER_ID`. There are two containers against which API calls can be made: the **global container** and the **tenant container**.

### Global container

The global container holds all standard Adobe and [!DNL Experience Platform] partner provided classes, mixins, data types, and schemas. You may only perform list and lookup (GET) requests against the global container.

An example of a call that uses the global container would look like the following:

```http
GET /global/classes
```

### Tenant container

Not to be confused with your unique `TENANT_ID`, the tenant container holds all classes, mixins, data types, schemas, and descriptors defined by an IMS Organization. These are unique to each organization, meaning they are not visible or manageable by other IMS Orgs. You may perform all CRUD operations (GET, POST, PUT, PATCH, DELETE) against resources that you create in the tenant container.

An example of a call that uses the tenant container would look like the following:

```http
POST /tenant/mixins
```

When you create a class, mixin, schema or data type in the tenant container, it is saved to the [!DNL Schema Registry] and assigned an `$id` URI that includes your `TENANT_ID`. This `$id` is used throughout the API to reference specific resources. Examples of `$id` values are provided in the next section.

## Schema identification {#schema-identification}

Schemas are identified with an `$id` attribute in the form of a URI, such as: 
* `https://ns.adobe.com/xdm/context/profile` 
* `https://ns.adobe.com/{TENANT_ID}/schemas/7442343-abs2343-21232421` 

To make the URI more REST-friendly, schemas also have a dot-notation encoding of the URI in a property called `meta:altId`:
* `_xdm.context.profile`
* `_{TENANT_ID}.schemas.7442343-abs2343-21232421`

Calls to the Schema Registry API will support either the URL-encoded `$id` URI or the `meta:altId` (dot-notation format). Best practice is to use the URL-encoded `$id` URI when making a REST call to the API, like so:
* `https%3A%2F%2Fns.adobe.com%2Fxdm%2Fcontext%2Fprofile`
* `https%3A%2F%2Fns.adobe.com%2F{TENANT_ID}%2Fschemas%2F7442343-abs2343-21232421`

## Accept header {#accept}

When performing list and lookup (GET) operations in the [!DNL Schema Registry] API, an Accept header is required to determine the format of the data returned by the API. When looking up specific resources, a version number must also be included in the Accept header.

The following table lists compatible Accept header values, including those with version numbers, along with descriptions of what the API will return when they are used.

| Accept | Description |
| ------- | ------------ |
| `application/vnd.adobe.xed-id+json` | Returns a list of IDs only. This is most commonly used for listing resources. |
| `application/vnd.adobe.xed+json` | Returns a list of full JSON schema with original `$ref` and `allOf` included. This is used to return a list of full resources. |
| `application/vnd.adobe.xed+json; version={MAJOR_VERSION}` | Raw XDM with `$ref` and `allOf`. Has titles and descriptions. |
| `application/vnd.adobe.xed-full+json; version={MAJOR_VERSION}` | `$ref` attributes and `allOf` resolved. Has titles and descriptions. |
| `application/vnd.adobe.xed-notext+json; version={MAJOR_VERSION}` | Raw XDM with `$ref` and `allOf`. No titles or descriptions. |
| `application/vnd.adobe.xed-full-notext+json; version={MAJOR_VERSION}` | `$ref` attributes and `allOf` resolved. No titles or descriptions. |
| `application/vnd.adobe.xed-full-desc+json; version={MAJOR_VERSION}` | `$ref` attributes and `allOf` resolved. Descriptors are included. |

>[!NOTE]
>
>If supplying the `major` version only (e.g. 1, 2, 3), the registry will return the latest `minor` version (e.g. .1, .2, .3) automatically.

## XDM field constraints and best practices

The fields of a schema are listed within its `properties` object. Each field is itself an object, containing attributes to describe and constrain the data that the field can contain. 

More information about defining field types in the API can be found in the [appendix](appendix.md) for this guide, including code samples and optional constraints for the most commonly used data types.

The following sample field illustrates a properly formatted XDM field, with further details on naming constraints and best practices provided below. These practices can also be applied when defining other resources that contain similar attributes.

```JSON
"fieldName": {
    "title": "Field Name",
    "type": "string",
    "format": "date-time",
    "examples": [
        "2004-10-23T12:00:00-06:00"
    ],
    "description": "Full sentence describing the field, using proper grammar and punctuation.",
}
```

* The name of a field object may contain alphanumeric, dash, or underscore characters, but **may not** start with an underscore.  
  * **Correct:** `fieldName`, `field_name2`, `Field-Name`, `field-name_3`  
  * **Incorrect:** `_fieldName`
* camelCase is preferred for the name of the field object. Example: `fieldName`
* The field should include a `title`, written in Title Case. Example: `Field Name`
* The field requires a `type`.  
    * Defining certain types may require an optional `format`.  
    * Where a specific formatting of data is required, `examples` can be added as an array.
    * The field type may also be defined using any data type in the registry. See the section on [creating a data type](create-data-type.md) in this guide for more information. 
* The `description` explains the field and pertinent information regarding field data. It should be written in full sentences with clear language so that anyone accessing the schema can understand the intention of the field.

See the [appendix](appendix.md) for more information how to define field types in the API.

## Next steps

This document covered the prerequisite knowledge required to make calls to the [!DNL Schema Registry] API, including required authentication credentials. You can now proceed to the sample calls provided in this developer guide and follow along with their instructions. For a full step-by-step walkthrough on how to make a schema in the API, please refer to the following [tutorial](../tutorials/create-schema-api.md). 
