---
keywords: Experience Platform;user guide;attribution ai;popular topics;region
solution: Experience Platform
title: Attribution AI user guide
topic: User guide 
description: This document serves as a guide for interacting with Attribution AI in the Intelligent Services user interface.

---

# Attribution AI user guide

Attribution AI, as part of Intelligent Services is a multi-channel, algorithmic attribution service that calculates the influence and incremental impact of customer interactions against specified outcomes. With Attribution AI, marketers can measure and optimize marketing and advertising spend by understanding the impact of every individual customer interaction across each phase of the customers’ journeys.

This document serves as a guide for interacting with Attribution AI in the Intelligent Services user interface.

## Create an instance

In the [!DNL Adobe Experience Platform] UI, click **Services** in the left navigation. The *Services* browser appears and displays available Adobe intelligent services. In the container for Attribution AI, click **Open**.

![Accessing your instance](./images/user-guide/open_Attribution_ai.png)

The Attribution AI service page appears. This page lists service instances of Attribution AI and displays information about them, including the name of the instance, conversion events, how often the instance is run, and the status of the last update. Click **Create instance** to begin.

![Create instance](./images/user-guide/landing_page.png)

Next, the setup page for Attribution AI appears, where you can provide basic information and specify a dataset for the instance.

![setup page](./images/user-guide/setup_attribution.png)

### Name the instance

Under *Basic information*, provide a name and optional description for your service instance.

![naming an instance](./images/user-guide/naming_instance.png)

### Select a dataset

After filling out the basic information, click the dropdown labeled **Select Dataset** to select your dataset. The dataset is used to train the model and score the subsequent data it produces. When selecting a dataset from the dropdown selector, only ones that are compatible with Attribution AI and conform to the Experience Data Model (XDM) schema are listed. Once a dataset is chosen, click **Next** in the top-right corner to proceed to the define events page.

![setup page](./images/user-guide/initial_creation_attribution.png)

## Defining events

There are three different types of input data used for defining events:

- **Conversion events:** Business objectives that identify the impact of marketing activities, such as, e-commerce orders, in-store purchases, and website visits.
- **Lookback window:** Provides a time frame indicating how many days prior to the conversion event touchpoints should be included.
- **Touchpoints:** recipient, individual, and or cookie-level marketing events used to evaluate the numeric or revenue-based impact of conversions.

### Define conversion events {#define-conversion-events}

In order to define a conversion event, you need to give the event a name and select the event type by clicking the **Enter Field Name** dropdown menu. 

![yes dropdown](./images/user-guide/conversion_event_2.png)

Once an event is selected, a new dropdown appears to its right. The second dropdown is used to provide further context to your event through the use of operations. For this conversion event, the default operation *exists* is used.

>[!NOTE]
>
>A string under your *conversion name* is updated as you define your event.

![no dropdown](./images/user-guide/conversion_event_1.png)

The *Add event* and *Add Group* buttons are used to further define your conversion. Depending on the conversion you are defining, you may need to use the *Add event* and *Add group* buttons to provide further context.

![add event](./images/user-guide/add_event.png)

Clicking **Add event** creates additional fields which can be filled using the same method as outlined above. Doing so adds an *AND* statement to the string definition below the *conversion name*. Click the **x** to remove an event that has been added.

![add event menu](./images/user-guide/add_event_result.png)

Clicking **Add Group** gives the option to create additional fields separate from the original. With the addition of groups, a blue *And* button appears. Clicking **And** gives an option to change the parameter to contain "Or". "Or" is used to define multiple successful conversion paths. "And" extends the conversion path to include additional conditions.

![using and or](./images/user-guide/and_or.png)

If you require more than one conversion, click **Add conversion** to create a new conversion card. You can repeat the process above to define multiple conversions.

![add conversion](./images/user-guide/add_conversion.png)

### Define lookback window {#lookback-window}

After you have finished defining your conversion, you need to confirm your lookback window. Using the arrow keys or by clicking the default value (56), specify how many days prior to your conversion event you wish to include touchpoints from. Touchpoints are defined in the next step.

![lookback](./images/user-guide/lookback_window.png)

### Define touchpoints

Defining touchpoints follows a similar workflow to [defining conversions](#define-conversion-events). Initially you need to name your touchpoint and select a touchpoint value from the *Enter Field Name* dropdown menu. Once selected, the operator dropdown appears with the default value "exists". Click the dropdown to reveal a list of operators.

![operators](./images/user-guide/operators.png)

For the purpose of this touchpoint, select **equals**.

![step 1](./images/user-guide/touchpoint_step1.png)

Once an operator for a touchpoint is selected, *Enter Field Value* is made available. The dropdown values for *Enter Field Value* populate based on the operator and touchpoint value you previously selected. If a value does not populate in the dropdown, you can type that value in manually. Click the dropdown and select **CLICK**.

>[!NOTE]
>
>The operators "exists" and "not exists" do not have field values associated with them.
 
![touchpoint dropdown](./images/user-guide/touchpoint_dropdown.png)

The *Add event* and *Add Group* buttons are used to further define your touchpoint. Due to the complex nature surrounding touchpoints, it is not uncommon to have multiple events and groups for a single touchpoint.

When clicked, **Add event** allows for additional fields to be added. Click the **x** to remove an event that has been added. 

![add event](./images/user-guide/touchpoint_add_event.png)

Clicking **Add group** gives you the option to create additional fields separate from the original. With the addition of groups, a blue *And* button appears. Click **And** to change the parameter, the new parameter "Or" is used to define multiple successful paths. This particular touchpoint only has one successful path, therefore "Or" is not needed.

![touchpoint overview](./images/user-guide/add_group_touchpoint.png)

>[!NOTE]
>
>Use the string under *Touchpoint name* for a quick overview of your touchpoint. Notice that the string matches the name of the touchpoint.

![](./images/user-guide/touchpoint_string.png)

You can add additional touchpoints by clicking **Add touchpoint** and repeating the process above.

![add touchpoint](./images/user-guide/add_touchpoint.png)

Once you have finished defining all necessary touchpoints, scroll up and click **Next** in the top-right corner to proceed to the final step.

![finished define](./images/user-guide/define_event_next.png)

## Advanced training and scoring setup

The final page in Attribution AI is the *Advanced* page used for setting up training and scoring.

![new page advanced](./images/user-guide/advanced_settings.png)

### Schedule training

Using the *Schedule*, you can select a day and time of the week you want scoring to take place. 

Click the dropdown under *Scoring Frequency* to select between daily, weekly, and monthly scoring. Next, select the days of the week you want the scoring to take place. Multiple days can be selected. Click a day a second time to deselect it.

![Schedule training](./images/user-guide/schedule_training.png)

To change the time of day you want scoring to occur, click the clock icon. In the new overlay that appears, enter the time of day you want scoring to take place. Click outside the overlay to close it.

>[!NOTE]
>
>It can take up to 24 hours for each scoring process to complete.

![clock icon](./images/user-guide/time_of_day.png)

### Region-based modeling (optional) {#region-based-modeling-optional}

Your customers' behaviors might differ significantly by country and geographic region. For global businesses, using country-based or region-based models can increase attribution accuracy. Each region added creates a new model with that region's data.

To define a new region, start by clicking **Add region**. In the container that appears, provide a name for the region. Only one value ("placeContext.geo.countryCode") populates from the *Enter Field Name* dropdown. Select this value.

![Select region att](./images/user-guide/select_region_att.png)

Next, select an operator. 

![region operator](./images/user-guide/region_operators.png)

Lastly, type in the country code in the *Enter Field Value* dropdown.

>[!NOTE]
>
>Country codes are two characters long. A complete list can be found here [ISO 3166-1 alpha-2](https://datahub.io/core/country-list).

![region](./images/user-guide/region-based.png)

### Training window {#training-window}

To ensure that you get the most accurate model possible, it is important to train your model with historical data that represents your business. By default, the model is trained using 2 quarters (6 months) of conversion events data. Select the dropdown to change the default. You can choose to train with one to four quarters of data (3-12 months).

>[!NOTE]
>
>A shorter training window is more sensitive to recent trends, whereas a longer training window creates a more robust model and is less sensitive to recent trends.

![training window](./images/user-guide/training_window.png)

Once you have selected your training window, click **Finish** in the top-right corner. Allow some time for the data to process. Once complete, a popover dialog appears confirming that the instance setup is complete. Click **Ok** to be redirected to the *Service instances* page where you can see your service instance.

![setup complete](./images/user-guide/instance_setup_complete.png)

## Next steps

By following this tutorial, you have successfully created a service instance in Attribution AI. Once the instance has finished scoring (allow up to 24 hours), you are ready to [discover Attribution AI insights](./discover-insights.md). Additionally, if you wish to download your scoring results, visit the [downloading raw scores](./download-scores.md) documentation.

## Additional resources

The following video outlines an end-to-end workflow for creating a new instance in Attribution AI.

>[!VIDEO](https://video.tv.adobe.com/v/32668?learn=on&quality=12)