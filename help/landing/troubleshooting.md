---
keywords: Experience Platform;home;popular topics
solution: Experience Platform
title: Adobe Experience Platform FAQ and Troubleshooting Guide
topic: getting started
---

# [!DNL Platform] FAQ and troubleshooting guide

This document provides answers to frequently asked questions about Adobe Experience Platform, as well as a high-level troubleshooting guide for common errors that may be encountered in any [!DNL Experience Platform] API. For troubleshooting guides on individual [!DNL Platform] services, see the [service troubleshooting directory](#service-troubleshooting-directory) below.

## FAQ {#faq}

The following is a list of answers to frequently asked questions about Adobe Experience Platform.

## What are [!DNL Experience Platform] APIs? {#what-are-experience-platform-apis}

[!DNL Experience Platform] offers multiple RESTful APIs that use HTTP requests to access [!DNL Platform] resources. These Service APIs each expose multiple endpoints, and allow you to perform operations to list (GET), lookup (GET), edit (PUT and/or PATCH), and delete (DELETE) resources. For more information on specific endpoints and operations available for each service, please see the [API Reference documentation](https://www.adobe.io/apis/experienceplatform/home/api-reference.html) on Adobe I/O.

## How do I format an API request? {#how-do-i-format-an-api-request}

Request formats vary depending on the [!DNL Platform] API being used. The best way to learn how to structure your API calls is by following along with the examples provided in the documentation for the particular [!DNL Platform] service you are using.

### Reading example API calls

The documentation for [!DNL Experience Platform] shows example API calls in two different ways. First, the call is presented in its **API format**, a template representation showing only the operation (GET, POST, PUT, PATCH, DELETE) and the endpoint being used (for example, `/global/classes`). Some templates also show the location of variables to help illustrate how a call should be formulated, such as `GET /{VARIABLE}/classes/{ANOTHER_VARIABLE}`.

The calls are then shown as cURL commands in a **Request**, which includes the necessary headers and full "base path" needed to successfully interact with the API. The base path should be pre-pended to all endpoints. For example, the aforementioned `/global/classes` endpoint becomes `https://platform.adobe.io/data/foundation/schemaregistry/global/classes`. You will see the API format / Request pattern throughout the documentation, and are expected to use the complete path shown in the example Request when making your own calls to Platform APIs.

### Example API request

The following is an example API request that demonstrates the format you will encounter in the documentation.

**API format**

The API format shows the operation (GET) and the endpoint being used. Variables are indicated by curly braces (in this case, `{CONTAINER_ID}`).

```http
GET /{CONTAINER_ID}/classes
```

**Request**

In this example request, the variables from the API format are given actual values in the request path. All required headers are shown as well, as either sample header values or variables where sensitive information (such as security tokens and access IDs) should be included.

```shell
curl -X GET \
  https://platform.adobe.io/data/foundation/schemaregistry/global/classes \
  -H 'Accept: application/vnd.adobe.xed-id+json' \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'x-sandbox-name: {SANDBOX_NAME}'
```

**Response**

The response illustrates what you would expect to receive following a successful call to the API, based on the request that was sent. Occasionally the response is truncated for space, meaning that you may see more information or additional information to that which is displayed in the sample.

```json
{
    "results": [
        {
            "title": "XDM ExperienceEvent",
            "$id": "https://ns.adobe.com/xdm/context/experienceevent",
            "meta:altId": "_xdm.context.experienceevent",
            "version": "1"
        },
        {
            "title": "XDM Individual Profile",
            "$id": "https://ns.adobe.com/xdm/context/profile",
            "meta:altId": "_xdm.context.profile",
            "version": "1"
        }
    ],
    "_links": {}
}
```

For more information on specific endpoints in Platform APIs, including required headers and request bodies, please see the [API Reference documentation](https://www.adobe.io/apis/experienceplatform/home/api-reference.html).

## What is my IMS organization? {#what-is-my-ims-organization}

An IMS organization is an an Adobe representation of a customer. Any licensed Adobe solutions are integrated with this customer organization. When an IMS organization is entitled to [!DNL Experience Platform], it can assign access to developers. The IMS Org ID (`x-gw-ims-org-id`) represents the organization that an API call should be executed for, and is therefore required as a header in all API requests. This ID can be found through the [Adobe Developer Console](https://www.adobe.com/go/devs_console_ui): in the **Integrations** tab, navigate to the **Overview** section for any particular integration to find the ID under **Client Credentials**. For a step-by-step walkthrough of how to authenticate into [!DNL Platform], see the [authentication tutorial](../tutorials/authentication.md).

## Where can I find my API key? {#where-can-i-find-my-api-key}

An API key is required as a header in all API requests. It can be found through the [Adobe Developer Console](https://www.adobe.com/go/devs_console_ui). Within the console, on the **Integrations** tab, navigate to the **Overview** section for a specific integration and you will find the key under **Client Credentials**. For a step-by-step walkthrough of how to authenticate to [!DNL Platform], see the [authentication tutorial](../tutorials/authentication.md).

## How do I get an access token? {#how-do-i-get-an-access-token}

Access tokens are required in the Authorization header of all API calls. They can be generated using a `curl` command, provided you have access to an integration for an IMS organization. Access tokens are only valid for 24 hours, after which a new token must be generated to continue using the API. For details on generating access tokens, see the [authentication tutorial](../tutorials/authentication.md).

## How do I use query parameters? {#how-do-i-user-query-parameters}

Some [!DNL Platform] API endpoints accept query parameters to locate specific information and filter the results returned in the response. Query parameters are appended to request paths with a question mark (`?`) symbol, followed by one or more query parameters using the format `paramName=paramValue`. When combining multiple parameters in a single call, you must use an ampersand (`&`) to separate individual parameters. The following example demonstrates how a request that uses multiple query parameters is represented in the documentation.

Examples of commonly used query parameters include:

```http
GET /tenant/schemas?orderby=title
GET /datasets?limit=36&start=10
GET /batches?createdAfter=1559775880000&orderBy=desc:created
```

For detailed information on which query parameters are available for a specific service or endpoint, please review the service-specific documentation.

## How do I indicate a JSON field to update in a PATCH request? {#how-do-i-indicate-a-json-field-to-update-in-a-patch-request}

Many PATCH operations in [!DNL Platform] APIs use [JSON Pointer](https://tools.ietf.org/html/rfc6901) strings to indicate JSON properties to update. These are typically included in request payloads using [JSON Patch](https://tools.ietf.org/html/rfc6902) format. See the [API fundamentals guide](api-fundamentals.md) for detailed information on required syntax for these technologies.

## Can I use Postman to make calls to [!DNL Platform] APIs? {#how-do-i-use-postman-to-make-calls-to-platform-apis}

[Postman](https://www.postman.com/) is a useful tool for visualizing calls to RESTful APIs. This [Medium post](https://medium.com/adobetech/using-postman-for-jwt-authentication-on-adobe-i-o-7573428ffe7f) describes how you can set up Postman to automatically perform authentication and use it to consume [!DNL Experience Platform] APIs.

## What are the system requirements for [!DNL Platform]? {#what-are-the-system-requirements-for-platform}

Depending on whether you are using the the UI or API, the following system requirements apply:

**For UI based operations:**
- A modern, standard web browser. While the latest version of [!DNL Chrome] is recommended, current and previous major releases of [!DNL Firefox], [!DNL Internet Explorer], and Safari are also supported.
    - Each time a new major version is released, [!DNL Platform] starts supporting the most recent version while support for the third most recent version is dropped.
- All browsers must have cookies and JavaScript enabled.

**For API and developer interactions:**
- A development environment to develop for REST, streaming, and Webhook integrations.

## Errors and troubleshooting {#errors-and-troubleshooting}

The following is a list of errors that you may encounter when using any [!DNL Experience Platform] service. For troubleshooting guides on individual [!DNL Platform] services, see the [service troubleshooting directory](#service-troubleshooting-directory) below.

## API status codes {#api-status-codes}

The following status codes may be encountered on any [!DNL Experience Platform] API. Each has a variety of causes, therefore the explanations given in this section are general in nature. For more details regarding specific errors in individual [!DNL Platform] services, please see the [service troubleshooting directory](#service-troubleshooting-directory) below.

Status Code | Description | Possible Causes
--- | --- | ---
400 | Bad request | The request was improperly constructed, missing key information, and/or contained incorrect syntax.
401 | Authentication failed | The request did not pass an authentication check. Your access token may be missing or invalid. See the [OAuth token errors](#oauth-token-is-missing) section below for more details.
403 | Forbidden | The resource was found, but you do not have the right credentials to view it.
404 | Not found | The requested resource could not be found on the server. The resource may have been deleted, or the requested path was entered incorrectly.
500 | Internal server error | This is a server-side error. If you are making many simultaneous calls, you may be reaching the API limit and need to filter your results. (See the [!DNL Catalog Service] API developer guide sub-guide on [filtering data](../catalog/api/filter-data.md) to learn more.) Wait for a moment before trying your request again, and contact your administrator if the problem persists.

## Request header errors {#request-header-errors}

All API calls in [!DNL Platform] require specific request headers. To see which headers are required for individual services, please see the [API Reference documentation](https://www.adobe.io/apis/experienceplatform/home/api-reference.html). To find the values for the required authentication headers, see the [Authentication tutorial](../tutorials/authentication.md). If any of these headers are missing or invalid when making an API call, the following errors may occur.

### OAuth token is missing {#oauth-token-is-missing}

```json
{
    "error_code": "403010",
    "message": "Oauth token is missing."
}
```

This error message displays when an `Authorization` header is missing from an API request. Ensure that the Authorization header is included with a valid access token before trying again.

### OAuth token is not valid

```json
{
    "error_code": "401013",
    "message": "Oauth token is not valid"
}
```

This error message displays when the provided access token in the `Authorization` header is not valid. Ensure that the token has been entered correctly, or [generate a new token](../tutorials/authentication.md) in the Adobe I/O Console.

### API key is required

```json
{
    "error_code": "403000",
    "message": "Api Key is required"
}
```

This error message displays when an API key header (`x-api-key`) is missing from an API request. Ensure that the header is included with a valid API key before trying again.

### API key is invalid

```json
{
    "error_code": "403003",
    "message": "Api Key is invalid"
}
```

This error message displays when the value of the provided API key header (`x-api-key`) is invalid. Ensure that you have entered the key correctly before trying again. If you do not know your API key, you can find it in the [Adobe I/O Console](https://console.adobe.io): in the **Integrations** tab, navigate to the **Overview** section for a specific integration to find the API key under **Client Credentials**.


### Missing header

```json
{
    "error_code": "400003",
    "message": "Missing header"
}
```

This error message displays when an IMS org header (`x-gw-ims-org-id`) is missing from an API request. Ensure that the header is included with the ID of your IMS organization before trying again.

### Profile is not valid

```json
{
    "error_code": "403025",
    "message": "Profile is not valid"
}
```

This error message displays when the user or Adobe I/O integration (identified by the [access token](#how-do-i-get-an-access-token) in the `Authorization` header) is not entitled to make calls to [!DNL Experience Platform] APIs for the IMS Org provided in the `x-gw-ims-org-id` header. Ensure that you have provided the correct ID for your IMS organization in the header before trying again. If you do not know your organization ID, you can find it in the [Adobe I/O Console](https://console.adobe.io): in the **Integrations** tab, navigate to the **Overview** section for a specific integration to find the ID under **Client Credentials**.

### Valid content-type not specified

```json
{
    "type": "/placeholder/type/uri",
    "status": 400,
    "title": "BadRequestError",
    "detail": "A valid content-type must be specified"
}
```

This error message displays when a POST, PUT or PATCH request has an invalid or missing `Content-Type` header. Ensure that the header is included in the request and that its value is `application/json`.


## Service troubleshooting directory {#service-troubleshooting-directory}

The following is a list of troubleshooting guides and API reference documentation for [!DNL Experience Platform] APIs. Each troubleshooting guide provides answers to frequently asked questions and solutions to problems that are specific to individual [!DNL Platform] services. The API reference documents provide a comprehensive guide to all available endpoints for each service, and show sample request bodies, responses, and error codes that you may receive.

|Service | API Reference | Troubleshooting|
--- | --- | ---
|Access Control | [Access Control API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/access-control.yaml) | [Access control troubleshooting guide](../access-control/troubleshooting-guide.md)|
|Catalog | [Catalog Service API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/catalog.yaml)||
|Data Ingestion (Batch)| [Data Ingestion API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/ingest-api.yaml) | [Batch ingestion troubleshooting guide](../ingestion/batch-ingestion/troubleshooting.md)|
|Data Ingestion (Streaming)|[Data Ingestion API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/ingest-api.yaml) | [Streaming ingestion troubleshooting guide](../ingestion/streaming-ingestion/troubleshooting.md)|
|Data Science Workspace | [Sensei Machine Learning API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/sensei-ml-api.yaml) | [Data Science Workspace troubleshooting guide](../data-science-workspace/troubleshooting-guide.md) |
|Data Usage Labeling and Enforcement (DULE) | [DULE Policy Service API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/dule-policy-service.yaml)||
|Experience Data Model (XDM) | [Schema Registry API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/schema-registry.yaml) | [XDM System FAQ and troubleshooting guide](../xdm/troubleshooting-guide.md)|
|Identity Service | [Identity Service API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/id-service-api.yaml) | [Identity Service troubleshooting guide](../identity-service/troubleshooting-guide.md)|
|Query Service | [Query Service API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/qs-api.yaml) | [Query Service troubleshooting guide](../query-service/troubleshooting-guide.md)|
|Real-time Customer Profile | [Real-time Customer Profile API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/real-time-customer-profile.yaml)||
|Sandboxes | [Sandbox API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/sandbox-api.yaml) | [Sandboxes troubleshooting guide](../sandboxes/troubleshooting-guide.md)|
| Segmentation | [Segmentation API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/segmentation.yaml) |
