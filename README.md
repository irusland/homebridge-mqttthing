[![npm](https://badgen.net/npm/v/@irusland/homebridge-mqttthing/latest)](https://www.npmjs.com/package/@irusland/homebridge-mqttthing)
[![npm](https://badgen.net/npm/dt/@irusland/homebridge-mqttthing)](https://www.npmjs.com/package/@irusland/homebridge-mqttthing)
[![Discord](https://img.shields.io/discord/432663330281226270?color=728ED5&logo=discord&label=discord)](https://discord.gg/MTpeMC)
[![verified-by-homebridge](https://badgen.net/badge/homebridge/verified/purple)](https://github.com/homebridge/homebridge/wiki/Verified-Plugins)

# Homebridge MQTT-Thing (TLS Fixed Version)
This is a fork of [Homebridge MQTT-Thing](https://www.npmjs.com/package/homebridge-mqttthing) with fixes for TLS configuration. The main changes are:

- Fixed TLS configuration to properly use top-level MQTT options
- Improved support for secure MQTT connections (mqtts://)
- Better handling of certificates and keys

## TLS Configuration Example
```json
{
  "accessory": "mqttthing",
  "type": "lightbulb",
  "name": "My Device",
  "url": "mqtts://your-broker:8883",
  "username": "your-username",
  "password": "your-password",
  "protocolId": "MQIsdp",
  "protocolVersion": 3,
  "rejectUnauthorized": false,
  "topics": {
    "setOn": "device/request"
  }
}
```

Note: MQTT options are now specified at the top level of the configuration, not inside an `mqttOptions` object.

# Homebridge MQTT-Thing
[Homebridge MQTT-Thing](https://www.npmjs.com/package/homebridge-mqttthing) is a plugin for [Homebridge](https://github.com/homebridge/homebridge) allowing the integration of [many different accessory types](#supported-accessories) using MQTT.

   * [Installation](#installation)
   * [Configuration](#configuration)
   * [Supported Accessories](#supported-accessories)
   * [Release notes](docs/ReleaseNotes.md)

## Alternatives

MQTT-Thing allows a wide range of Homekit accessory types to be integrated using MQTT, and has some quite flexible configuration options which are very helpful in many scenarios. However, if you want quick and simple integration with Zigbee devices exposed through Zigbee2MQTT you should also consider the [z2m plugin](https://z2m.dev/).

## Compatibility with previous versions

**From version 1.1.45, MQTT-Thing requires Node.js 16 or later.**

**From version 1.1.x, raw JavaScript values for Boolean properties are passed to MQTT apply functions.** This may change published message formats, e.g. when apply functions are used to build JSON strings.

For full details of changes please see the [Release notes](docs/ReleaseNotes.md).

## Installation
Follow the instructions in [homebridge](https://www.npmjs.com/package/homebridge) for the homebridge server installation.
This plugin is published through [NPM](https://www.npmjs.com/package/homebridge-mqttthing) and should be installed "globally" by typing:

    npm install -g homebridge-mqttthing

Installation through 
[Homebridge Config UI X](https://www.npmjs.com/package/homebridge-config-ui-x) is also supported (and recommended).

## Configuration
Configure the plugin in your homebridge `config.json` file. Most configuration settings can now also be entered using 
[Homebridge Config UI X](https://www.npmjs.com/package/homebridge-config-ui-x).

MQTT topics used fall into two categories:

   * Control topics, of the form `setXXX`, are published by MQTT-Thing in order to control device state (e.g. to turn on a light).
   * Status/notification topics, of the form `getXXX`, are published by the device to notify MQTT-Thing that something has occurred (e.g. that a sensor has detected something or a control topic action has been performed).

For further details, see [docs/Configuration.md](docs/Configuration.md) and [docs/Codecs.md](docs/Codecs.md).

## Supported Accessories

The following Homekit accessory types are supported by MQTT-Thing:

   * [Air Pressure Sensor](docs/Accessories.md#air-pressure-sensor)
   * [Air Purifier](docs/Accessories.md#air-purifier)
   * [Air Quality Sensor](docs/Accessories.md#air-quality-sensor)
   * [Carbon Dioxide Sensor](docs/Accessories.md#carbon-dioxide-sensor)
   * [Carbon Monoxide Sensor](docs/Accessories.md#carbon-monoxide-sensor)
   * [Contact Sensor](docs/Accessories.md#contact-sensor)
   * [Door](docs/Accessories.md#door)
   * [Doorbell](docs/Accessories.md#doorbell)
   * [Fan](docs/Accessories.md#fan)
   * [Fanv2](docs/Accessories.md#fanv2)
   * [Garage door opener](docs/Accessories.md#garage-door-opener)
   * [Heater Cooler](docs/Accessories.md#heater-cooler)
   * [Humidity Sensor](docs/Accessories.md#humidity-sensor)
   * [Irrigation System](docs/Accessories.md#irrigation-system)
   * [Leak Sensor](docs/Accessories.md#leak-sensor)
   * [Light bulb](docs/Accessories.md#light-bulb)
   * [Light Sensor](docs/Accessories.md#light-sensor)
   * [Lock Mechanism](docs/Accessories.md#lock-mechanism)
   * [Microphone](docs/Accessories.md#microphone)
   * [Motion Sensor](docs/Accessories.md#motion-sensor)
   * [Occupancy Sensor](docs/Accessories.md#occupancy-sensor)
   * [Outlet](docs/Accessories.md#outlet)
   * [Security System](docs/Accessories.md#security-system)
   * [Speaker](docs/Accessories.md#speaker)
   * [StatelessProgrammableSwitch](docs/Accessories.md#statelessprogrammableswitch)
   * [Switch](docs/Accessories.md#switch)
   * [Television](docs/Accessories.md#television)
   * [Temperature Sensor](docs/Accessories.md#temperature-sensor)
   * [Thermostat](docs/Accessories.md#thermostat)
   * [Valve (Sprinkler, Shower, Faucet)](docs/Accessories.md#valve)
   * [Weather Station](docs/Accessories.md#weather-station)
   * [Window](docs/Accessories.md#window)
   * [Window Covering (Blinds)](docs/Accessories.md#window-covering)
   
## Tested Configurations

Tested and working configurations for devices are available on the [Wiki](https://github.com/arachnetech/homebridge-mqttthing/wiki/Tested-Configurations).  Please add your working configurations for others.
