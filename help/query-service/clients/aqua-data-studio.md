---
keywords: Experience Platform;home;popular topics;query service;Query service;Aqua Data Studio;Aqua data studio;connect to query service;
solution: Experience Platform
title: Connect with Aqua Data Studio
topic: connect
---

# Connect with [!DNL Aqua Data Studio]

This document walks through the steps for connecting [!DNL Aqua Data Studio] with Adobe Experience Platform [!DNL Query Service].

After installing [!DNL Aqua Data Studio], you must first register the server. From the main menu, click **[!UICONTROL Server]**, then click **[!UICONTROL Register Server]**.

![](../images/clients/aqua-data-studio/register-server.png)

The **[!UICONTROL Register Server]** dialog appears. Under the **[!UICONTROL General]** tab, select **[!UICONTROL PostgreSQL]** from the list on the left-hand side. In the dialog that appears, provide the following details for the server settings.

- **[!UICONTROL Name]**: The name of your connection.
- **[!UICONTROL Login Name and Password]**: The login credentials that will be used. The username takes the form of `ORG_ID@AdobeOrg`.
- **[!UICONTROL Host and Port]**: The host endpoint and its port for [!DNL Query Service]. 
- **[!UICONTROL Database]:** The database that will be used.

>[!NOTE]
>
>For more information on finding your login credentials, host, port, and database name, visit the [credentials page on Platform](https://platform.adobe.com/query/configuration). To find your credentials, log in to [!DNL Platform], click **[!UICONTROL Queries]**, then click **[!UICONTROL Credentials]**.

![](../images/clients/aqua-data-studio/register-server-general-tab.png)

Select the **[!UICONTROL Driver]** tab. Under **[!UICONTROL Parameters]**, set the value as `?sslmode=require`

![](../images/clients/aqua-data-studio/register-server-driver-tab.png)

After inputting your connection details, click **[!UICONTROL Test Connection]** to ensure your credentials work properly. If your connection is successful, click **[!UICONTROL Save]** to register your server. The connection appears on the *Dashboard* upon successful registration, confirming that you can now connect to the server and view its schema objects.

## Next Steps

Now that you have connected to [!DNL Query Service], you can use the **[!UICONTROL Query Analyzer]** within [!DNL Aqua Data Studio] to execute and edit SQL statements. For more information on how to write and run queries, please read the [running queries guide](../creating-queries/creating-queries.md).