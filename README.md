# ha-bosch-thermostat-sync
A Home Assistant Blueprint to reliably sync external temperature sensors with Bosch Radiator Thermostats II, featuring battery-optimized heartbeat updates and precision triggering

## About this Blueprint
Many users experience issues with **Bosch Radiator Thermostats II** not updating correctly when using external temperature sensors via Zigbee2MQTT or ZHA. This blueprint provides a robust solution by implementing a dual-logic approach:

* **Reliable Heartbeat**: Forces a temperature update every 5 minutes to prevent the thermostat from falling back to its internal sensor ("sleeping" bug).
* **Precision Triggering**: Immediately pushes new data if the external sensor detects a change of 0.1°C or more.
* **Battery Efficient**: Uses intelligent conditions to avoid redundant Zigbee traffic, significantly extending the battery life of your thermostats.
* **Group Support**: Seamlessly works with multiple thermostats in a single room while maintaining full compatibility with HomeKit-grouped climate entities.
