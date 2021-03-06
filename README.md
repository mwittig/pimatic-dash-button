[![Build Status](http://img.shields.io/travis/michbeck100/pimatic-dash-button/master.svg)](https://travis-ci.org/michbeck100/pimatic-dash-button)
[![Version](https://img.shields.io/npm/v/pimatic-dash-button.svg)](https://img.shields.io/npm/v/pimatic-dash-button.svg)
[![downloads][downloads-image]][downloads-url]

[downloads-image]: https://img.shields.io/npm/dm/pimatic-dash-button.svg?style=flat
[downloads-url]: https://npmjs.org/package/pimatic-dash-button

pimatic-dash-button
=======================

pimatic-dash-button is a [pimatic](https://github.com/pimatic/pimatic) plugin that enables Amazon's dash button to be used as push button device.

#### Installation

Since this plugin uses [node-pcap](https://github.com/mranney/node_pcap), libpcap-dev must be installed on a raspberry pi:

    sudo apt-get install libpcap-dev

To install the plugin just add the plugin to the config.json of pimatic:

```json
{
  "plugin": "dash-button"   
}
```

This will fetch the most recent version from npm-registry on the next pimatic start and install the plugin.

###### Dash Button installation

Follow the instructions in the Amazon app to configure your button, to connect to your wifi but **don't select a product in the last step. Just exit the app**.  Optionally disable the internet access for your dash button in your router configuration, otherwise the Amazon app might complain the incomplete setup of your dash button, every time you press it.

#### Configuration

pimatic-dash-button supports the device discovery feature of pimatic (as of version 0.9.x). To create a new dash button device, just click on "Discover devices" in the Devices section of pimatic.
Once the discovery mode is on, press the dash button and it should show up as a new discovered device. If you have any issues discovering your dash button please report [here](https://github.com/michbeck100/pimatic-dash-button/issues).

To manually add a dash button to your configuration just add it to the devices section including the mac address:

```json
"devices": [
  {
    "id": "dash_button",
    "class": "DashButtonDevice",
    "name": "Dash Button",
    "address": "aa:bb:cc:dd:ee:ff"
  }
]
```

If you have multiple network interfaces on your hardware and pimatic has issues finding your dash button, then configure the plugin to explicitly to use a defined interface.

```json
{
  "plugin": "dash-button",
  "interface": "eth0"   
}
```

### Sponsoring

Do you like this plugin? Then consider a donation to support development.

<span class="badge-paypal"><a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2T48JXA589B4Y" title="Donate to this project using Paypal"><img src="https://img.shields.io/badge/paypal-donate-yellow.svg" alt="PayPal donate button" /></a></span>
[![Flattr pimatic-dash-button](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=michbeck100&url=https://github.com/michbeck100/pimatic-dash-button&title=pimatic-dash-button&language=&tags=github&category=software)

### Changelog
0.1.0
* [#2](https://github.com/michbeck100/pimatic-dash-button/issues/2) Dash button device acts like a ButtonsDevice now, fixes issues with pimatic-mobile-frontend. Device can now be used in UI, too.
* [#3](https://github.com/michbeck100/pimatic-dash-button/issues/3) Decreased buffer size of pcap to 1 MB
* [#4](https://github.com/michbeck100/pimatic-dash-button/issues/4) Filtering for mac addresses directly in libpcap on kernel level

0.0.2
* bugfix for mac address filtering

0.0.1
* initial release

### Credit
Most of the dash button discovery code was inspired by [node-dash-button](https://github.com/hortinstein/node-dash-button) and [node-pcap](https://github.com/mranney/node_pcap).
