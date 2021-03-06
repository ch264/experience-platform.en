---
keywords: Experience Platform;home;popular topics
solution: Experience Platform
title: Create an Azure File Storage source connector in the UI
topic: overview
---

# Create an [!DNL Azure File Storage] source connector in the UI

>[!NOTE]
>The [!DNL Azure File Storage] connector is in beta. See the [Sources overview](../../../../home.md#terms-and-conditions) for more information on using beta-labelled connectors.

Source connectors in Adobe Experience Platform provide the ability to ingest externally sourced data on a scheduled basis. This tutorial provides steps for authenticating an [!DNL Azure File Storage] source connector using the [!DNL Platform] user interface.

## Getting started

This tutorial requires a working understanding of the following components of Adobe Experience Platform:

-   [Experience Data Model (XDM) System](../../../../../xdm/home.md): The standardized framework by which [!DNL Experience Platform] organizes customer experience data.
    -   [Basics of schema composition](../../../../../xdm/schema/composition.md): Learn about the basic building blocks of XDM schemas, including key principles and best practices in schema composition.
    -   [Schema Editor tutorial](../../../../../xdm/tutorials/create-schema-ui.md): Learn how to create custom schemas using the Schema Editor UI.
-   [Real-time Customer Profile](../../../../../profile/home.md): Provides a unified, real-time consumer profile based on aggregated data from multiple sources.

If you already have a File Storage connection, you may skip the remainder of this document and proceed to the tutorial on [configuring a dataflow](../../dataflow/batch/cloud-storage.md).

### Gather required credentials

In order to authenticate your [!DNL Azure File Storage] source connector, you must provide values for the following connection properties:

| Credential | Description |
| ---------- | ----------- |
| `host` | The endpoint of the [!DNL Azure File Storage] instance you are accessing. |
| `userId` | The user with sufficient access to the [!DNL Azure File Storage] endpoint. |
| `password` | The [!DNL Azure File Storage] access key. |

For more information about getting started refer to [this Azure File Storage document](https://docs.microsoft.com/en-us/azure/storage/files/storage-how-to-use-files-windows).

## Connect your [!DNL Azure File Storage] account

Once you have gathered your required credentials, you can follow the steps below to create a new [!DNL Azure File Storage] account to connect to [!DNL Platform].

Log in to [Adobe Experience Platform](https://platform.adobe.com) and then select **[!UICONTROL Sources]** from the left navigation bar to access the *[!UICONTROL Sources]* workspace. The *[!UICONTROL Catalog]* screen displays a variety of sources for which you can create an inbound account with, and each source shows the number of existing accounts and dataflows associated with them.

You can select the appropriate category from the catalog on the left-hand side of your screen. Alternatively, you can find the specific source you wish to work with using the search option.

Under the *[!UICONTROL Databases]* category, select **[!UICONTROL Azure File Storage]** click **on the + icon (+)** to create a new Azure File Storage connector.

![catalog](../../../../images/tutorials/create/azure-file-storage/catalog.png)

The *[!UICONTROL Connect to Azure File Storage]* page appears. On this page, you can either use new credentials or existing credentials.

### New account

If you are using new credentials, select **[!UICONTROL New account]**. On the input form that appears, provide the connection with a name, an optional description, and your File Storage credentials. When finished, select **[!UICONTROL Connect]** and then allow some time for the new account to establish.

![connect](../../../../images/tutorials/create/azure-file-storage/new.png)

### Existing account

To connect an existing account, select the [!DNL Azure File Storage] account you want to connect with, then select **[!UICONTROL Next]** to proceed.

![existing](../../../../images/tutorials/create/azure-file-storage/existing.png)

## Next steps

By following this tutorial, you have established a connection to your [!DNL Azure File Storage] account. You can now continue on to the next tutorial and [configure a dataflow to bring data from your cloud storage into Platform](../../dataflow/batch/cloud-storage.md).