---
name: New UniFi Device
about: Request Support for a New UniFi Device
title: "[New Device] UniFi Device Name"
labels: enhancement
assignees: MassimilianoPasquini97

---

## Context

- UniFi Device Type: `UAP, UDM, USW, ...`
- UniFi Device Name: `Provide UniFi Device name with store url`

## New Features

A clear and concise description of what items or trigger you want to implement for this new UniFi Device.

## JSON

Follow this steps for retrive JSON data for the new device.

1. Create a file named `auth.json` containing Unifi credential. Replace {$UNIFI.USERNAME} and {$UNIFI.PASSWORD} with your credential. User must be a local user and is preferred to not use the same used by Zabbix.

```json
{
    "username": "{$UNIFI.USERNAME}",
    "password": "{$UNIFI.PASSWORD}"
}
```

2. Get authentication cookie with the following command. Replace {$UNIFI.IP} and '/api/auth/login' with 'api/login' if you are using Unifi vm instead of Dream Machine.

```shell
curl -k -X POST -d @auth.json -c cookie --header 'Content-Type: application/json' https://{$UNIFI.IP}/api/auth/login
```

3. Get data for the new UniFi Device with the following command. Replace {$UNIFI.IP}, {$UNIFI.UAP.MAC} with macaddress of the New Device with following format "AA:AA:AA:AA:AA:AA" and remove '/proxy/network' if you are using Unifi vm instead of Dream Machine.

```shell
curl -k -X GET -b cookie --header 'Content-Type: application/json' https://{$UNIFI.IP}/proxy/network/api/s/default/stat/device/{$UNIFI.UAP.MAC}
```


```json
```
