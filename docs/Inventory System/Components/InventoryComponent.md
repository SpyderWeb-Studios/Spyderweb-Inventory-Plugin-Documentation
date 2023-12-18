---
sidebar_label: 'Inventory Component'
sidebar_position: 3
---

# Inventory Component

## Adding Item to Inventory

Call `AddItemToInventory` with an object to add and the quantity that you'd like to attempt to add. You
can control if the item can be added with the `CanAddItemToInventory` function that you can override in both
C++ and Blueprint. 

By default, it will verify that the execution is on the server, the item is valid and implements
the [`ItemUsageInterface`](/docs/Inventory%20System/Interfaces/ItemUsageInterface.md). This is done to verify that the
item supports the functionality required from an inventory item. If it does not implement this interface, it will
check if it implements the [`InventoryItemInterface](/docs/Inventory%20System/Interfaces/InventoryItemInterface.md), which
can be used to link to another item which might be what is being added. In other words, you can pass in an item that
will not pass the checks but have it link to a valid inventory item which will be added instead. 

 You can also define if an item can be added in the actual Item Class itself, via the 
 [`ItemUsageInterface`](/docs/Inventory%20System/Interfaces/ItemUsageInterface)

:::warning
This function node is `BlueprintAuthorityOnly`. This means that it will only enter the execution if it is on the 
machine with authority, either the listen server, dedicated server or in standalone. It will not execute if it called 
on the server. 
:::

After this point, it will attempt to add the item. It will do this recursively until either the item quantity is 0 or 
when the Inventory fills up. After each slot that has been added to, it will call the K2_OnItemAdded function so you can 
add any additional functionality without risking breaking the existing architecture. 

:::tip

Use the Built in Event `OnItemAddedToInventoryDelegate` to build event driven functionality and to make sure that your
UI responds as efficiently as possible. See how this is done on the WB_InventoryPanel.

:::


## Removing Item From Inventory

You can remove an item by Object, Class or by Slot (and by Class & Slot simultaneously). 

:::warning

This function node is `BlueprintAuthorityOnly`. This means that it will only enter the execution if it is on the
machine with authority, either the listen server, dedicated server or in standalone. It will not execute if it called
on the server.

:::

Compared to the adding item to Inventory functions, it is quite simple. It does still have the overridable functions
on both the component and the item, to define if this item can be removed from the inventory. A good use case for this 
would be if you have a quest item that once picked up, should not be able to be removed until the quest line is complete.

:::tip

If the Item is successfully removed from the Inventory, it will call the `K2_OnItemRemovedFromInventory` for the 
blueprint children. You can also use the `OnItemRemovedFromInventoryDelegate` for your UI and to build up the event
driven behaviour. 

:::
## Transferring Item


## Using Item


