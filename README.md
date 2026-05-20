Bosch Thermostat External Sensor Sync (BTH-RA)
A robust Home Assistant Blueprint to reliably sync external temperature sensors (e.g., Sonoff, Aqara) with Bosch Radiator Thermostats II.

🚀 The Problem
Many users notice that Bosch thermostats "ignore" external temperature updates via Zigbee2MQTT or ZHA if the value stays stable for too long or if the update intervals are too wide. This leads to the thermostat falling back to its internal sensor, causing inaccurate heating.

✨ The Solution
This blueprint implements a Dual-Logic Sync:

Reliable Heartbeat: Forces a sync every 5 minutes (Time Pattern) to keep the connection alive and prevent the "sleeping bug".

Precision Triggering: Updates immediately if the external sensor detects a change of 0.1°C or more.

Battery Efficient: Intelligent conditions prevent redundant Zigbee traffic, significantly extending battery life.

Group Support: Effortlessly syncs a single sensor to multiple thermostats in one room—perfect for HomeKit-grouped setups.

🛠 Updates
Version 1.1.0 – Improved Stability: The blueprint now features enhanced robustness against temporary sensor connection issues. By adding default values (float(0)) to all temperature template filters, the automation handles unknown sensor states gracefully, preventing unnecessary errors in your Home Assistant log.

📊 Proof of Concept
The automation ensures a seamless update history. Even when the temperature is stable, the Time Trigger fills the gaps to maintain the remote temperature link:

16:05:01 - Updated to 18.1°C (Triggered by Time Pattern)

15:49:42 - Updated to 18.2°C (Triggered by Temperature Change)

🛠 Installation
Click the "Import Blueprint" button above.

In Home Assistant, go to Settings -> Automations -> Blueprints.

Click Import Blueprint and follow the instructions.

Create a new automation, select your external sensor and your Bosch thermostat(s).

Note: If you are upgrading from an older version and notice log errors, simply re-import the blueprint to apply the latest fixes.
