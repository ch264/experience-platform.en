---
keywords: Experience Platform;home;popular topics;Paypal;paypal;PayPal
solution: Experience Platform
title: PayPal connector
topic: overview
description: The documentation below provides information on how to connect PayPal to Platform using APIs or the user interface.
---

# (Beta) [!DNL PayPal] connector

>[!NOTE]
>
>The [!DNL PayPal] connector is in beta. See the [Sources overview](../../home.md#terms-and-conditions) for more information on using beta-labelled connectors.

Adobe Experience Platform allows data to be ingested from external sources while providing you with the ability to structure, label, and enhance incoming data using [!DNL Platform] services. You can ingest data from a variety of sources such as Adobe applications, cloud-based storage, databases, and many others.

[!DNL Experience Platform] provides support for ingesting data from a third-party payments application. Support for payments providers include [!DNL PayPal].

## IP address allow list

The following IP addresses must be added to an allow list prior to working with source connectors. Failing to add your region-specific IP addresses to your allow list may lead to errors or non-performance when using sources.

### East US region

- `20.41.2.0/23`
- `20.41.4.0/26`
- `20.44.17.80/28`
- `20.49.102.16/29`
- `40.70.148.160/28`
- `52.167.107.224/28`

### West Europe region

- `13.69.67.192/28`
- `13.69.107.112/28`
- `13.69.112.128/28`
- `40.74.24.192/26`
- `40.74.26.0/23`
- `40.113.176.232/29`
- `52.236.187.112/28`

### Australia East

- `13.70.74.144/28`
- `20.37.193.0/25`
- `20.37.193.128/26`
- `20.37.198.224/29`
- `40.79.163.80/28`
- `40.79.171.160/28`

The documentation below provides information on how to connect [!DNL PayPal] to [!DNL Platform] using APIs or the user interface:

## Connect [!DNL PayPal] to [!DNL Platform] using APIs

- [Create a PayPal connector using the Flow Service API](../../tutorials/api/create/payments/paypal.md)
- [Explore a payments application using the Flow Service API](../../tutorials/api/explore/payments.md)
- [Collect data from a payments application using the Flow Service API](../../tutorials/api/collect/payments.md)

## Connect [!DNL PayPal] to [!DNL Platform] using the UI

- [Create a PayPal source connector in the UI](../../tutorials/ui/create/payments/paypal.md)
- [Configure a dataflow for a payments connector in the UI](../../tutorials/ui/dataflow/payments.md)