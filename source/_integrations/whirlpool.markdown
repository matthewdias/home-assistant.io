---
title: Whirlpool Appliances
description: Instructions on how to integrate Whirlpool appliances with Home Assistant.
ha_category:
  - Binary sensor
  - Button
  - Climate
  - Hub
  - Select
ha_release: '2022.10'
ha_iot_class: Cloud Push
ha_config_flow: true
ha_codeowners:
  - '@abmantis'
  - '@mkmer'
ha_domain: whirlpool
ha_platforms:
  - binary_sensor
  - button
  - climate
  - diagnostics
  - select
  - sensor
ha_integration_type: hub
ha_quality_scale: silver
---

The **Whirlpool Appliances** {% term integration %} allows you to connect Whirlpool, Maytag, KitchenAid, and Consul appliances to Home Assistant.

## Supported devices

The following appliances are confirmed to be working, but other models may also work.

Air conditioners:

- Whirlpool SPIW309A2WF
- Whirlpool SPIW312A2WF
- Whirlpool SPIW409A2WF

Washers:

- Whirlpool WTW6120HW2
- Whirlpool WTW8127LW1
- Maytag MHW8630HW0

Dryers:

- Whirlpool WGD8127LW3

## Prerequisites

- Valid Whirlpool (or related brand) account credentials.
- Registered appliances in the official Whirlpool (or related brand) mobile app.

{% include integrations/config_flow.md %}

{% configuration_basic %}
Username:
    description: "The username of your Whirlpool (or related brand) account."
Password:
    description: "The password of your Whirlpool (or related brand) account."
Region:
    description: "The region in which your account is registered."
Brand:
    description: "The brand of the mobile app. It may or may not be the same brand as the appliances."
{% endconfiguration_basic %}

## Supported functionality

This {% term integration %} maps appliances to entities in Home Assistant. A single appliance may be represented by one or more entities.

- [Binary Sensor](#binary-sensor)
- [Button](#button)
- [Climate](#climate)
- [Select](#select)
- [Sensor](#sensor)

### Binary Sensor

The binary sensor platform provides the following functionality:

- state of the washer/dryer machine door (open/closed)

### Button

The button platform provides the following functionality:

- stop the current cooking program for an oven cavity

### Climate

The `whirlpool` climate platform integrates Whirlpool air conditioning systems into Home Assistant, allowing control of the appliance through the user interface. The current inside temperature and humidity are also displayed on the thermostat card.

The following actions are also available:

- [**set_hvac_mode**](/integrations/climate/#action-set-hvac-mode) (`off`, `heat`, `cool`, `fan_only`)
- [**target temperature**](/integrations/climate/#action-set-temperature)
- [**turn on/off**](/integrations/climate/#action-turn-on)
- [**fan mode**](/integrations/climate/#action-set-fan-mode) (`low`, `medium`, `high`)
- [**swing mode**](/integrations/climate/#action-set-swing-mode) (`off`, `horizontal`)

### Select

The select platform provides the following entity for refrigerators:

- **Temperature level**: Sets the temperature level of the refrigerator. The available options are `-4 °C`, `-2 °C`, `0 °C`, `3 °C`, and `5 °C`.

### Sensor

The `whirlpool` sensor platform provides the following entities.

Washers and dryers:

- **State**: Shows the current machine state.
- **End time**: Shows when the current cycle is expected to finish.

Washers also have a **Detergent level** sensor for the "wash & go" feature. This sensor is disabled by default.

Ovens:

- **State**: Shows the current state of the oven cavity.
- **Cook mode**: Shows the active cooking mode for the cavity.
- **Current temperature**: Shows the current temperature of the oven cavity.
- **Target temperature**: Shows the target temperature set for the oven cavity.

Ovens with two cavities have separate state, cook mode, current temperature, and target temperature sensors for the upper and lower cavity.

## Removing the integration

This integration follows standard integration removal. No extra steps are required.

{% include integrations/remove_device_service.md %}
