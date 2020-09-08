---
keywords: RTCDP;CDP;Real-time Customer Data Platform;real time customer data platform;real time cdp;cdp;destinations;destination;rtcdp
title: Destinations Overview
seo-title: Destinations Overview
description: Destinations are pre-built integrations with destination platforms that allow for the seamless activation of data from Real-time Customer Data Platform. You can use Destinations in the Adobe Real-time Customer Data Platform to activate your known and unknown data for cross-channel marketing campaigns, email campaigns, targeted advertising, and many other use cases.
seo-description: Destinations are pre-built integrations with destination platforms that allow for the seamless activation of data from Real-time Customer Data Platform. You can use Destinations in the Adobe Real-time Customer Data Platform to activate your known and unknown data for cross-channel marketing campaigns, email campaigns, targeted advertising, and many other use cases.
---

# [!DNL Destinations] overview {#overview}

![Destinations overview banner](/help/rtcdp/destinations/assets/destinations-overview-banner.png)

**[!DNL Destinations]** are pre-built integrations with destination platforms that allow for the seamless activation of data from Real-time Customer Data Platform. You can use destinations to activate your known and unknown data for cross-channel marketing campaigns, email campaigns, targeted advertising, and many other use cases.

## Destinations and Sources {#destinations-and-sources}

One of the core functionalities of Real-time CDP is ingesting your first-party data and activating it for your business needs. Use sources to ingest data into Real-time CDP and destinations to export data from Real-time CDP. 

## Destinations steps {#steps}

* Choose from a [self-service catalog](/help/rtcdp/destinations/destinations-catalog.md) of all the destinations available in Real-time CDP.
* Use **[!UICONTROL Destinations]** to [activate](/help/rtcdp/destinations/activate-destinations.md) and send profiles or segments to marketing automation platforms, digital advertising platforms, and more.
* Schedule data exports to your preferred destinations at regular times.

## Controls {#controls}

The controls in the [Destinations workspace](/help/rtcdp/destinations/destinations-workspace.md) allow you to:

* Browse the catalog of destination platforms where you can activate your data;
* Create, edit, activate, and disable data flows to the destinations in the catalog;
* Create an account in a storage location or link Real-time CDP to the account in the destination platform;
* Select which segments should be activated to destinations;
* Select which [Experience Data Model (XDM) fields](../../xdm/home.md) to export when activating segments to email marketing destinations.

## Destination types and categories {#types-and-categories}

For detailed information, see the [destination types and categories overview](/help/rtcdp/destinations/destination-types.md).

## Destinations and Access Controls {#access-controls}

The destinations functionality in Real-time CDP works with Adobe Experience Platform access control permissions. Depending on your user's permission level, you can view, manage, and activate destinations. For information about the individual permissions, see [Access control in Adobe Experience Platform](../../access-control/home.md) and scroll down to the bottom of the page.

For more information about access controls, see the [Access control user guide](../../access-control/ui/overview.md).

## [!DNL Data Governance] restrictions on activating data to destinations {#data-governance}

Data governance is enforced for Real-time CDP destinations through:

* *Marketing use cases* that you can select in the create destinations workflow;
* *Data usage policies* that restrict data containing certain usage labels from being activated to destinations with certain marketing use cases.
  
See the [!DNL Data Governance] in Real-time CDP documentation for more information about [marketing use cases](/help/rtcdp/privacy/data-governance-overview.md#destinations) and [resolving data policy violations](/help/rtcdp/privacy/data-governance-overview.md#enforcement).

For more information about selecting marketing use cases in the create destination workflow, see the following pages for the different destination types in Real-time CDP:

* [Advertising destinations - Google Ad Manager ](/help/rtcdp/destinations/google-ad-manager-destination.md)
* [Advertising destinations - Google Ads](/help/rtcdp/destinations/google-ads-destination.md)
* [Advertising destinations - Google Display & Video 360 ](/help/rtcdp/destinations/google-dv360-destination.md)
* [Cloud storage destinations](/help/rtcdp/destinations/cloud-storage-destinations-workflow.md)
* [Email marketing destinations](/help/rtcdp/destinations/email-marketing-destinations.md)
* [Social network destinations](/help/rtcdp/destinations/social-network-destinations-workflow.md)

For more information about data policy violations in the segment activation workflow, see the Review step in [Activate profiles and segments to a destination](/help/rtcdp/destinations/activate-destinations.md#review).