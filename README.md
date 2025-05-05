<p align="center">
    <img src="docs/image/logo.webp" height="128" alt="Unifi Network Zabbix Template">
</p>
<h1 align="center">Unifi Network Zabbix Template</h1>

This template is designed to monitor Unifi network devices using Unifi Network API.  A special thanks those who created and maintain this [wiki page](https://ubntwiki.com/products/software/unifi-controller/api).  This guide helped me create this template.

- [Supported Unifi Devices](#supported-unifi-devices)
- [Features](#features)
- [How to use](#how-to-use)
- [Contribute](#contribute)
- [License](#license)

## Supported Unifi Devices

| Type | Description         |
| ---- | ------------------- |
| udm  | Unifi Dream Machine |
| uxg  | UXG Gateway         |
| usw  | Unifi Switch        |
| uap  | Unifi Access Point |

## Features

General:

- Unifi Controller CPU usage.
- Unifi Controller Memory usage.
- Unifi device status (Active, Disabled, Disconnected and Pending Adoption) for Switches and Access Points.
- Unifi Controller LAN, WLAN, VPN, and GUEST online client counters.
- Unifi Controller WAN metrics.
- Advanced metrics for all active LAN and WLAN clients.

UDM:

- CPU usage.
- Memory usage.
- Temperature sensors.
- Metrics for all ports.
- Other metrics.

UXG:

- CPU usage.
- Memory usage.
- Temperature sensors.
- Metrics for all ports.
- Other metrics.

USW:

- CPU usage.
- Memory usage.
- Metrics for all ports.
- Other metrics.

UAP:

- CPU usage.
- Memory usage.
- Wireless metrics.
- Other metrics.

## How to use

1. Create a local user with *view only* permission on the Unifi Controller using the Unifi Controller web interface.  Zabbix will use this user to access the Unifi Network API.

2. Import the template file ***zbx_template_unifi_network.yaml*** into Zabbix.

3. Create a new host in Zabbix and link the ***Unifi Network*** template.  

4. Configure these macros:

    - ***{$UNIFI.IP}***: IP or FQDN of Unifi Controller web interface.
    - ***{$UNIFI.USERNAME}***: Username of View Only user.
    - ***{$UNIFI.PASSWORD}***: Password of View Only user.
    - ***{$UNIFI.API.AUTH.URI}***: change to `api/login` if using the Unifi Controller application & not a Unifi Dream Machine.
    - ***{$UNIFI.API.AUTH.TOKEN}***: change to `unifises` if using the Unifi Controller application & not a Unifi Dream Machine.
    - ***{$UNIFI.API.URI}***: change to `api/s/default/stat` if using the Unifi Controller application & not a Unifi Dream Machine.

    *Other macros included in the template may be edited to customize trigger parameters.*

    If you've done everything right, Zabbix will auto discover Unifi Dream Machines, UXG Gateways, Unifi Switches, and Unifi Access Points and create an host object for each.

### Changing the Unifi site ID

By default, the template is configured to monitor the `default` Unifi site. If you want to monitor a different site, change `default` to the site ID in the `{$UNIFI.API.URI}` macro. The site ID can be found in the URL used to access the Unifi Controller web interface.

### Monitoring multiple sites

To monitor multiple sites, create separate Zabbix hosts, each with a distinct `{$UNIFI.API.URI}` macro value.

## Contribute

This template is in an early stage and can be improved to support other Unifi devices. Feel free to fork and submit pull request. 🙏🏻

## License

Licensed under the [MIT license](https://github.com/MassimilianoPasquini97/zbx_unifi_network/blob/main/LICENSE.md).
