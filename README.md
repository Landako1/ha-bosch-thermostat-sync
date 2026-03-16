# Bosch Thermostat External Sensor Sync (BTH-RA)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/Landako1/ha-bosch-thermostat-sync/blob/main/blueprints/automation/bosch_thermostat_sync.yaml)

A robust Home Assistant Blueprint to reliably sync external temperature sensors (e.g., Sonoff, Aqara) with **Bosch Radiator Thermostats II**. 

## 🚀 The Problem
Many users notice that Bosch thermostats "ignore" external temperature updates via Zigbee2MQTT or ZHA if the value stays stable for too long or if the update intervals are too wide. This leads to the thermostat falling back to its internal sensor, causing inaccurate heating.

## ✨ The Solution
This blueprint implements a **Dual-Logic Sync**, as proven in real-world testing (see logs below):

* **Reliable Heartbeat**: Forces a sync every **5 minutes** (Time Pattern) to keep the connection alive and prevent the "sleeping bug".
* **Precision Triggering**: Updates immediately if the external sensor detects a change of **0.1°C** or more.
* **Battery Efficient**: Intelligent conditions prevent redundant Zigbee traffic, significantly extending battery life.
* **Group Support**: Effortlessly syncs a single sensor to multiple thermostats in one room—perfect for HomeKit-grouped setups.

## 📊 Proof of Concept
The automation ensures a seamless update history. Even when the temperature is stable, the **Time Trigger** fills the gaps to maintain the remote temperature link:

* *16:05:01* - Updated to **18.1°C** (Triggered by **Time Pattern**)
* *15:49:42* - Updated to **18.2°C** (Triggered by **Temperature Change**)

## 🛠 Installation

1. Click the **"Import Blueprint"** button above or copy the URL of the `.yaml` file.
2. In Home Assistant, go
