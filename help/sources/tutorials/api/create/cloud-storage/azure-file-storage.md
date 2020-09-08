---
keywords: Experience Platform;home;popular topics;Azure;Azure File Storage;Azure file storage
solution: Experience Platform
title: Create an Azure File Storage connector using the Flow Service API
topic: overview
description: This tutorial uses the Flow Service API to walk you through the steps to connect Azure File Storage to Experience Platform.
---

# Create an [!DNL Azure File Storage] connector using the [!DNL Flow Service] API

>[!NOTE]
>
>The [!DNL Azure File Storage] connector is in beta. See the [Sources overview](../../../../home.md#terms-and-conditions) for more information on using beta-labelled connectors.

[!DNL Flow Service] is used to collect and centralize customer data from various disparate sources within Adobe Experience Platform. The service provides a user interface and RESTful API from which all supported sources are connectable.

This tutorial uses the [!DNL Flow Service] API to walk you through the steps to connect [!DNL Azure File Storage] to [!DNL Experience Platform].

## Getting started

This guide requires a working understanding of the following components of Adobe Experience Platform:

*   [Sources](../../../../home.md): [!DNL Experience Platform] allows data to be ingested from various sources while providing you with the ability to structure, label, and enhance incoming data using [!DNL Platform] services.
*   [Sandboxes](../../../../../sandboxes/home.md): [!DNL Experience Platform] provides virtual sandboxes which partition a single [!DNL Platform] instance into separate virtual environments to help develop and evolve digital experience applications.

The following sections provide additional information that you will need to know in order to successfully connect to [!DNL Azure File Storage] using the [!DNL Flow Service] API.

### Gather required credentials

In order for [!DNL Flow Service] to connect with [!DNL Azure File Storage], you must provide values for the following connection properties:

| Credential | Description |
| ---------- | ----------- |
| `host` | The endpoint of the [!DNL Azure File Storag]e instance you are accessing. |
| `userId` | The user with sufficient access to the [!DNL Azure File Storage] endpoint. |
| `password` | The password for your [!DNL Azure File Storage] instance |
| Connection specification ID | The unique identifier needed to create a connection. The connection spec ID for [!DNL Azure File Storage] is: `be5ec48c-5b78-49d5-b8fa-7c89ec4569b8` |

For more information about getting started refer to [this Azure File Storage document](https://docs.microsoft.com/en-us/azure/storage/files/storage-how-to-use-files-windows).

### Reading sample API calls

This tutorial provides example API calls to demonstrate how to format your requests. These include paths, required headers, and properly formatted request payloads. Sample JSON returned in API responses is also provided. For information on the conventions used in documentation for sample API calls, see the section on [how to read example API calls](../../../../../landing/troubleshooting.md#how-do-i-format-an-api-request) in the [!DNL Experience Platform] troubleshooting guide.

### Gather values for required headers

In order to make calls to [!DNL Platform] APIs, you must first complete the [authentication tutorial](../../../../../tutorials/authentication.md). Completing the authentication tutorial provides the values for each of the required headers in all [!DNL Experience Platform] API calls, as shown below:

*   Authorization: Bearer `{ACCESS_TOKEN}`
*   x-api-key: `{API_KEY}`
*   x-gw-ims-org-id: `{IMS_ORG}`

All resources in [!DNL Experience Platform], including those belonging to the [!DNL Flow Service], are isolated to specific virtual sandboxes. All requests to [!DNL Platform] APIs require a header that specifies the name of the sandbox the operation will take place in:

*   x-sandbox-name: `{SANDBOX_NAME}`

All requests that contain a payload (POST, PUT, PATCH) require an additional media type header:

*   Content-Type: `application/json`

## Create a connection

A connection specifies a source and contains your credentials for that source. Only one connection is required per Azure File Storage account as it can be used to create multiple source connectors to bring in different data.

**API format**

```http
POST /connections
```

**Request**

The following request creates a new [!DNL Azure File Storage] connection, configured by the properties provided in the payload:


```shell
curl -X POST \
    'https://platform.adobe.io/data/foundation/flowservice/connections' \
    -H 'Authorization: Bearer {ACCESS_TOKEN}' \
    -H 'x-api-key: {API_KEY}' \
    -H 'x-gw-ims-org-id: {IMS_ORG}' \
    -H 'x-sandbox-name: {SANDBOX_NAME}' \
    -H 'Content-Type: application/json' \
        -d '{
        "name": "Azure File Storage connection",
        "description": "An Azure File Storage test connection",
        "auth": {
            "specName": "Basic Authentication",
            "params": {
                    "host": "{HOST}",
                    "userId": "{USER_ID}",
                    "password": "{PASSWORD}"
                }
        },
        "connectionSpec": {
            "id": "be5ec48c-5b78-49d5-b8fa-7c89ec4569b8",
            "version": "1.0"
        }
    }'
```

| Property | Description |
| --------- | ----------- |
| `auth.params.host` | The endpoint of the [!DNL Azure File Storage] instance you are accessing.. |
| `auth.params.userId` | The user with sufficient access to the [!DNL Azure File Storage] endpoint. |
| `auth.params.password` | The [!DNL Azure File Storage] access key. |
| `connectionSpec.id` | The [!DNL Azure File Storage] connection specification ID: `be5ec48c-5b78-49d5-b8fa-7c89ec4569b8`. |

**Response**

A successful response returns details of the newly created connection, including its unique identifier (`id`). This ID is required to explore your data in the next tutorial.

```json
{
    "id": "f9377f50-607a-4818-b77f-50607a181860",
    "etag": "\"2f0276fa-0000-0200-0000-5eab3abb0000\""
}
```

## Next steps

By following this tutorial, you have created an [!DNL Azure File Storage] connection using the [!DNL Flow Service] API and have obtained the connection's unique ID value. You can use this ID in the next tutorial as you learn how to [explore a third-party cloud storage using the Flow Service API](../../explore/cloud-storage.md).
