# Zabbix templates for Vectra Platform

## Overview

The template to monitor The Vectra Platform by Zabbix v.6.4 using HTTP Agent.

This template was tested on Vectra Quadrant UX Platform:

- version 7.x
- version 8.x

Tested with the following form-factor:

- X29
- X80
- B101
- AWS
- vmware

> [!IMPORTANT]  
> This template has not been tested with Vectra Respond UX platform but content is similar. Only the authentication medthod (oauth2) and API URL Path have changed.

## Setup

> See [Zabbix templates importing](https://www.zabbix.com/documentation/current/en/manual/xml_export_import/templates) for basic instructions on how to import a template.

Create a Vectra Brain host and link this template to it. Two macros are being used:

  - **{$API_KEY}**: Vectra's API key (My profile > API Token)
  - **{$HOST}**: Vectra Brain Hostname (or IP address)

> The required permission in the role is: **View > Health**

## Discovery rules

The template uses a LLD rule to identify all sensors connected to a Brain.

|Name|Type|Description|Key|
|----|----|----------------|--------|
|Sensor Discovery |`HTTP agent`|<p>Discovery for sensor name, serial number and LUID</p> |vectra.discovery.sensors|

## Items collected

All items are gathered using a unified API endpoint. A **parent item** serves as the basis for retrieving data, while various dependent items are utilized to gather diverse elements.

|Name|Type|Description|
|----------|----|--------------|
|Version|`HTTP agent`|<p>Uptime of Vetcra Brain</p> |
|Uptime|`HTTP agent`|<p>Currently installed version of Vectra</p> |
|Model|`HTTP agent`|<p>Hardware model for Vectra's Brain</p> |
|Power Status|`HTTP agent`|<p>Vectra Brain Power supply status</p> |
|Power Message|`HTTP agent`|<p>Vectra Brain Power supply message</p> |
|CPU Idle|`HTTP agent`|<p>Vectra Brain: Idle CPU</p> |
|CPU System|`HTTP agent`|<p>Vectra Brain: System CPU</p> |
|CPU User|`HTTP agent`|<p>Vectra Brain: User CPU</p> |
|Disk Raid status|`HTTP agent`|<p>Vectra Brain RAID status</p> |
|Disk Raid message|`HTTP agent`|<p>Vectra Brain RAID status message</p> |
|Disk Utilization: Usage percent|`HTTP agent`|<p>Vectra's Brain RAID disk usage (percentage)</p> |
|Disk Utilization: Total bytes|`HTTP agent`|<p>Vectra's Brain RAID disk: Total bytes</p> |
|Disk Utilization: Free bytes|`HTTP agent`|<p>Vectra's Brain RAID disk: Free bytes</p> |
|Disk Utilization: Used bytes|`HTTP agent`|<p>Vectra's Brain RAID disk: Used bytes</p> |
|Memory usage|`HTTP agent`|<p>Vectra's Brain Memory usage (percentage)</p> |
|Memory total bytes|`HTTP agent`|<p>Vectra Brain Memory: Total bytes</p> |
|Memory free bytes|`HTTP agent`|<p>Vectra Brain Memory: Free bytes</p> |
|Memory used bytes|`HTTP agent`|<p>Vectra Brain Memory: Used bytes</p> |
|Memory error|`HTTP agent`|<p>Vectra's Brain Memory error message</p> |
|Brain Network interface status: eth0|`HTTP agent`|<p>Vectra Brain eth0 interface status</p> |
|Brain Network interface status: eth1|`HTTP agent`|<p>Vectra Brain eth1 interface status</p> |
|Brain Network interface status: eth2|`HTTP agent`|<p>Vectra Brain eth2 interface status</p> |
|Brain Network interface status: eth3|`HTTP agent`|<p>Vectra Brain eth3 interface status</p> |
|Connectivity Status for sensor {#SENSORNAME}|`HTTP agent`|<p>Sensor status/p> |
|Pairing status for sensor {#SENSORSN}|`HTTP agent`|<p>Sensor pairing status/p> |
|Connectivity Status for sensor {#SENSORNAME}|`HTTP agent`|<p>Sensor status/p> |
|Interface status for sensor {#SENSORLUID} for eth0|`HTTP agent`|<p>Sensor interface status (eth0)/p> |
|Last check for sensor {#SENSORNAME}|`HTTP agent`|<p>Last time the sensor connects back to the brain /p> |
|Message for sensor {#SENSORNAME}|`HTTP agent`|<p>Status message from sensor /p> |
|Aggregated Peak Traffic for sensor {#SENSORNAME}|`HTTP agent`|<p>Aggregated traffic stats from sensor/p> |
|Traffic drop status for sensor {#SENSORNAME}|`HTTP agent`|<p>Traffic drop status from sensor/p> |
|Traffic drop message for sensor {#SENSORNAME}|`HTTP agent`|<p>Traffic drop message from sensor/p> |


> Based on the Vectra Brain's form-factor, certain items will not be compatible and must be deactivated. Tags have been assigned to items to distinguish those that are specific to the platform. This is a one-time configuration.

## Triggers

Appropriate triggers are associated with the items

## Graphs

|Name|Description|
|----------|--------------|
|CPU|<p>Vectra Brain CPU stats</p> |
|Disk usage|<p>Vectra Brain Disk stats</p> |
|Aggregated Peak Traffic|<p> Aggregated Peak Traffic for all sensors</p> |

## Feedback

Please report any issues with the template here in the "Issues" tab.