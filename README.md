<p align="center">
    <img src="docs/image/logo.webp" height="128">
    <h1 align="center">Unifi Network Zabbix Template</h1>
</p>

This template is meant for monitoring Unifi network devices using Unifi Network API. Special thanks who wrote and maintain this [wiki page](https://ubntwiki.com/products/software/unifi-controller/api), this guide helped me for realizing this template.

- [Supported Unifi Devices](#supported-unifi-devices)
- [Features](#features)
- [How to use](#how-to-use)
- [Contribute](#contribute)
- [License](#license)

## Supported Unifi Devices

| Type | Description         |
| ---- | ------------------- |
| udm  | Unifi Dream Machine |
| usw  | Unifi Switch        |
| uap  | Unifi Acccess Point |

## Features

General:

- Unifi Controller CPU usage.
- Unifi Controller Memory usage.
- Unifi Active, Disabled, Disconnected and Pending Switch and Access Point.
- Unifi Controller LAN, WLAN, VPN and GUEST online client counter.
- Unifi Controller WAN metrics.
- Advanced metrics for all active client on WLAN and LAN.

UDM:

- CPU usage.
- Memory usage.
- Temperature sensors.
- Metrics for al ports.
- Other metrics.

USW:

- CPU usage.
- Memory usage.
- Metrics for al ports.
- Other metrics.

UAP:

- CPU usage.
- Memory usage.
- Wireless metrics.
- Other metrics.

## How to use

First of all you need to import the template file ***zbx_template_unifi_network.yaml*** in Zabbix. 😅

Said that, this template use Unifi Network API so it need a view only local user on Unifi Network Web Interface.

Once you create view only user, on Zabbix create a new host and link ***Unifi Network*** template, those macros need to be configured:

- ***{$UNIFI.IP}***: IP or FQDN of Unifi Network Web Interface.
- ***{$UNIFI.USERNAME}***: Username of View Only user.
- ***{$UNIFI.PASSWORD}***: Password of View Only user.
- ***{$UNIFI.API.AUTH.URI}***: change to `api/login` if using unifi controller vm
- ***{$UNIFI.API.AUTH.TOKEN}***: change to `unifises` if using unifi controller vm
- ***{$UNIFI.API.URI}***: change to `api/s/default/stat` if using unifi controller vm

If you prefer you can modify other macros for further personalize trigger parameters.

If you done all right now it auto discover all Unifi Dream Machine, Unifi Switch and Unifi Access Point and create an host object for all of them.

### Monitoring multiple sites

By default, this template is configured for monitoring the `default` site. If you want to monitor a different site, swap `default` with the site ID from the `{$UNIFI.API.URI}` macro. To monitor multiple sites, create separate Zabbix hosts each with a distinct `{$UNIFI.API.URI}` macro value. Finding the site ID is straightforward, access your Unifi console in a browser, navigate to the site you want to monitor, and look for the site ID on the URL.

## Contribute

This template is on early stage and can bee improved supporting other Unifi devices. Feel free to fork and submit pull request. 🙏🏻

## License

Licensed under the [MIT license](https://github.com/MassimilianoPasquini97/zbx_unifi_network/blob/main/LICENSE.md).
