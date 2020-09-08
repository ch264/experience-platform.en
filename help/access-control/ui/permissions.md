---
keywords: Experience Platform;home;popular topics;product profile;manage permissions
solution: Experience Platform
title: Manage permissions for a product profile
topic: user guide
description: Access control in Adobe Experience Platform allows you to manage roles and permissions for various Platform capabilities by using the Adobe Admin Console. This document serves as a guide for how to manage permissions for a product profile for Platform.
---

# Manage permissions for a product profile

Immediately after [creating a new product profile](#create-a-new-product-profile), you are prompted to configure the profile's permissions. If you are editing permissions for an existing profile, select the profile from the **[!UICONTROL Product Profiles]** tab to open the profile's details page, then click **[!UICONTROL Permissions]**.

![profile-permissions](../images/profile-permissions.png)

Permissions are divided into categories and listed on this page. The list displays the category name, the number of permissions it contains (and how many are active), and its description.

Click any category on the list to open the *Edit Permissions* page.

![edit-permissions](../images/edit-permissions.png)

The **[!UICONTROL Edit Permissions]** page provides a workspace to add and remove permissions from the selected product profile. The left side of the screen displays a list of permission categories. Clicking a category changes the permissions that are displayed under **[!UICONTROL Available Permissions Items]**.

![change-permissions-category](../images/change-permissions-category.png)

To add a permission, click the **plus (+)** icon next to the permission's name. Alternatively, you can click **[!UICONTROL Add all]** to add all permissions under the current category to the profile. Added permissions appear under **[!UICONTROL Included Permission Items]**.

![add-permissions](../images/add-permissions.png)

>[!NOTE]
>
>The **[!UICONTROL Included Permissions Items]** list only displays added permissions from the currently selected category.

To remove a permission, click the **X** icon next to the permission's name, or select **[!UICONTROL Remove all]** to remove all permissions under the current category. Removed permissions reappear under **[!UICONTROL Available Permission Items]**.

Continue going through the available categories and adding any desired permissions. When finished, click **[!UICONTROL Save]**.

![permissions-finish](../images/permissions-finish.png)

The **[!UICONTROL Permissions]** tab for the product profile reappears, and shows that the selected permissions are now active.

![added-permissions](../images/added-permissions.png)

## Next steps

With permissions established, you can proceed to the next step to [manage details and services for a product profile](details-and-services.md)