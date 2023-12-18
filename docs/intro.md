# Overview

## Spyderweb Studios: Multiplayer Modular Inventory & Crafting System

This plugin was designed to be as easy and approachable to use without sacrificing
on the power and capabilities. It uses C++ on the backend with Unreal Engines FastArray
so the only the data that was changed will be replicated, minimising the bandwidth and
latency.

This website is built using [Docusaurus](https://docusaurus.io/), a modern static website generator.

This plugin can provide you with a wide range of systems that often required
for a variety of different games and can offer you the flexibility needed to
make something unique. It is designed to be modular and with the end goal of
functionality and ease of integration into an existing project.


### Interactable System Features
This is the most basic module included in the Plugin, and holds
functionality that will most likely already be in the target project
already.

- Fully Networked Interact Component:
  - Can interact with any item required they have the
    interact interface implemented
- Interact Interface:
  - ObjectAttemptInteract allows any object to attempt
    to interact with any other. This approach tends to utilise
    an interface based codebase, great for modularity and integration.

### Inventory System Features

- Fully Replicated Inventory Component:
  - Feature Set:
    - Adding and Removing Items
    - Transferring Items between Inventories
    - Using Items
    - Dropping Items
  - Utility Functions to retrieve data about the current
    inventory and the current state of it
  - Events for when the state of the inventory changes,
    that work on both Server and Client
######
- Items:
  - Can be defined as individual assets, so
    can be loaded separately.
  - Different Item Class for different behaviour
  - Interfaces to retrieve information
  - Separates the Inventory Items from the Actors,
    to lessen the network load whilst maintaining functionality
######

### Crafting System Features

- Fully Replicated Crafting Component:
  - Feature Set:
    - Manages the Player's crafting
      ability and is the main point of entry into the system

- Recipe Management Component:
  - Feature Set:
    - Manages what Recipes can be crafted at any particular
      point
    - Different Actors can have different Recipe Sets without
      any modification. So you can have a crafting bench and anvil
      completely separate crafting behaviour and recipes and no problems
######

- Recipes:
  - Can be defined as individual assets, so
    can be loaded separately
  - Interfaces to retrieve information
  - Separates the Inventory Items from the Actors,
    to lessen the network load whilst maintaining functionality
  