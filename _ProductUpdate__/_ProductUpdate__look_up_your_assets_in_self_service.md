---
title: "Look Up Your Assets in Self Service"
date: "November 4, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/look-up-your-assets-in-self-service"
slug: "look-up-your-assets-in-self-service"
---

# Look Up Your Assets in Self Service

End users are now able to look up the assets that their organization has made available to them.  When they open [Xurrent Self Service](https://www.xurrent.com/features/self-service-portal) or the [Xurrent App](https://www.xurrent.com/product-updates/download-the-4me-app), they will see a new option in the menu.  This option is called ‘My Assets’.

The ‘My Assets’ menu option is available only when the user’s person record is linked to at least one [configuration item](https://help.xurrent.com/help/configuration_item/).  When this menu option is selected, the user will see a list of his or her configuration items.

Selecting one of the assets takes the user to a screen that provides a little more information about the asset, specifically the support team and the date since when the asset is in use.

The date since when the asset is in use corresponds with the Start date field of the configuration item record in Xurrent’s configuration management database ([CMDB](https://www.xurrent.com/features/service-configuration-and-it-asset-management)).  This may be useful in organizations that allow their employees to order a replacement PC or phone after a specific number of years.

More important, though, is the **Submit Request for This Asset** button.  This button makes it easy for end users to obtain support for one of the assets they use.  Pressing this button takes the user to the list of standard requests and knowledge articles that could be relevant for the selected asset (or rather, for the service of the [service instance](https://help.xurrent.com/help/service_instance/) that the configuration item is a part of).

Selecting one of the standard requests (i.e. a [request template](https://help.xurrent.com/help/request_template/)) makes it easy for the user to provide all the information needed by the specialists to complete the request.  Alternatively, a knowledge article can be selected so that the user does not even need to contact the support organization.

If the account administrator activated the **None of the Above** button in the [Self Service Settings](https://www.xurrent.com/product-updates/self-service-settings), the end user can press this button to provide a subject and a short description before submitting a new request.  The new request is then related to the configuration item and the configuration item’s service instance, and it will be assigned to the first line team of this service instance, or the support team of the service instance if the First line team field of the service instance is empty.
