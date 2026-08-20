---
title: "Introducing Custom Collections"
date: "October 6, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-custom-collections"
slug: "introducing-custom-collections"
---

# Introducing Custom Collections

Most Xurrent customers make use of the ability to add custom fields to Xurrent’s user interface.  To do this, they define [UI extensions](https://www.xurrent.com/blog/advanced-ui-extension-examples) for specific types of requests, changes, configuration items, etc.  Some of the fields they add require users to select an option.  For example, when requesting a new laptop or software license, the user may be asked to select a cost center.

The challenge organizations face is that the list of options behind a custom field can be quite long, these options may need to be obtained from other systems (such as SAP or Oracle Finance), and they may change routinely.

To help organizations address this challenge, Xurrent is introducing the concept of custom collections.  Custom collections make it possible to store long lists of items in a Xurrent account, automate the maintenance of these lists, and create custom fields that allow users to make a selection from these items.  Because some of these lists are expected be very long, the custom fields in which these items can be selected behave as [suggest fields](https://www.xurrent.com/blog/see-why-suggestions-are-offered), allowing users to search for an item within these fields.

Before a custom suggest field can be added to a UI extension, administrators need to prepare the list of options for it.  To explain how this is done, let’s assume that a large multinational wants to classify all the facilities in which it operates by adding a custom suggest field to its site records.

The first step for the [designer](https://help.xurrent.com/help/account_designer_role) or [administrator](https://help.xurrent.com/help/account_administrator_role) is to define a new custom collection in the ‘Custom Collections’ section of the Settings console.  A custom collection is used to group the field options together.  A new custom collection can be defined by simply giving it a name.  Xurrent then generates its unique reference.  A description can be added to explain to other designers and administrators what the custom collection is used for.

After creating the custom collection, it is possible only for an administrator to add custom collection elements to it.  These elements are the values users will be able to select in the custom suggest fields that make use of the custom collection.  Custom collection elements can be added and maintained manually in the Settings console.  Specifying a short name for each element is sufficient.  Xurrent automatically generates a reference for each element.

When there are lots of elements to add, however, it is better to import them using Xurrent’s [Import API](https://developer.xurrent.com/v1/import/).  The Import API can also be used to maintain the custom collection elements.  To keep the elements in sync with another system in near real-time, Xurrent’s [GraphQL API](https://developer.xurrent.com/graphql/object/customcollectionelement/) is available.

For some elements it may make sense to add a picture.  That may later help users when they need to choose an element.  To upload a picture for an element, open it in Edit mode, click on the icon and select an image file.

After the custom collection elements have been loaded, it is time to define a custom view.  A custom view is used to specify which elements need to become available for selection when the custom view is used by a custom suggest field.

Having defined a custom view, it becomes possible to add a custom suggest field to a UI extension and to link this custom suggest field to the custom view.

To do this, a designer or administrator goes to the ‘UI Extensions’ section of the Settings console and opens a new or existing UI extension.  The Snippets feature can then be used to add a custom field of the type ‘custom-suggest’ to the UI extension.  This allows the new custom field to be linked to the custom view.

These steps are all pretty easy, but it is important to follow them in this order.  The result is a custom field that makes it easy for users to find the option they are looking.

When the list is very long, e.g. when there are hundreds of thousands of options, users can still easily find the one they are looking for by simply entering a few characters of an element’s name or description.

It is important to point out that it is possible to create custom collections in all types of Xurrent accounts, including directory accounts.  Once a custom view is defined for a custom collection in a directory account, this custom view can be used by a custom suggest field that is created in one of the directory account’s support domain accounts.

This makes it easy, for example, to centrally maintain all cost centers of an enterprise and share them with all the support domain accounts of this enterprise.  The designers and administrators of these support domain accounts can then add a cost center field to a UI extension that is linked to a request template or product so that users can select a cost center in certain standard requests, or configuration managers can link a cost center to specific types of configuration items.

In multilingual support environments where customers need to be able to use Xurrent Self Service in their preferred language, it may be necessary to translate the name and description of the custom collection elements.  As with other record types, this can be done in the ‘Translations’ section of the Settings console.  There, Xurrent’s [auto translation functionality](https://www.xurrent.com/blog/introducing-auto-translation-for-translators) proposes translations to assist translators.

**Advanced Use of Custom Collections**

But there’s more to explain about this new capability.  A custom collection element is essentially a record like any other Xurrent record.  Using the UI extensions functionality, it is possible to add custom fields to the custom collection element form for specific custom collections.

Sticking with our example of the custom collection ‘Site Types’, let’s assume that the checkbox ‘Hazardous workplace’ needs to be added to its elements.  To realize this, a UI extension will need to be defined for custom collections.

Once the first UI extension has been activated for custom collections, it is possible to link it to a custom collection.  Linking a UI extension to a specific custom collection causes the custom fields of the UI extension to become available in all elements of the custom collection.

The result is visible when one of the custom collection’s elements is opened in Edit mode.

Having this additional field available in the elements, allows automation rules to make use of it.  For example, an automation rule could be created to perform a specific action after someone has selected a site in the UI extension of a request and the site type of this site has a check in its ‘Hazardous workplace’ box.

This may already sound a little advanced, but it is possible to take this one step further.  Custom views can not only be created for custom collection elements; they can also be defined for most of the standard record types that are available in Xurrent, such as products, knowledge articles, service offerings, skill pools, time allocations, etc.

This makes it possible, for example, to define a custom view that lists only the managers who are authorized to approve expenditures.

The custom view above assumes that all managers belong to the skill pool ‘Managers’ and that those with financial approval authority are marked as a VIP.  Applying such filters to a custom view limits the options that are available for selection when the custom view is linked to a custom suggest field.

It may be good to quickly point out here that all filters that are available in the views of a record type are also available for its custom views.  This means that any [filterable custom field](https://www.xurrent.com/product-updates/custom-field-filters) of a record type can be used to define custom views for this record type.

Having created the custom view, a UI extension can be created for a custom collection.  This UI extension can include a custom suggest field that uses the custom view.  If we assume that the organization has already loaded its cost centers as custom collection elements, the UI extension can be used to link approvers to these cost centers.

The values of a cost center’s custom fields can then be used by automation rules to determine who to assign the approval task to after a request for purchasing new equipment for a specific cost center has been submitted.

There were already a few UI extension field types that could be used to create custom suggest fields in which a Xurrent record could be selected.  Those field types are:

- organization-suggest
- person-suggest
- site-suggest
- team-suggest

It is important to understand the difference between these custom field types and custom suggest fields that make use of a custom view of the same record type.  The difference is that the options users can select in the four UI extension fields types that were already available before is determined by the records the user is allowed to see.  The options that a user is allowed to select in the new custom suggest fields is dictated by the custom view that is used by the custom suggest field.

The new custom suggest fields therefore make it possible to allow users to select records they are not authorized to see.  That can be useful, for example, when someone uses a request template to request a service he/she is not covered for.  A custom suggest field that uses a custom view of the organization’s service records can now be created for this purpose.
