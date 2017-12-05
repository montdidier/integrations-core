# Reboot Required

## Overview

Linux systems that are configured to autoinstall packages may not be configured to autoreboot (it may be desirable to time this manually). This check will enable alerts to be fired in the case where reboots are not performed in a timely manner.

## Installation

The directory check is packaged with the Agent, so simply [install the Agent](https://app.datadoghq.com/account/settings#agent) anywhere you wish to use it.

## Configuration

1. Edit your `reboot_required.yaml` file in the Agent's `conf.d` directory. See the [sample reboot_required.yaml](https://github.com/DataDog/integrations-core/blob/master/reboot_required/conf.yaml.example) for all available configuration options:

## Validation

[Run the Agent's `info` subcommand](https://help.datadoghq.com/hc/en-us/articles/203764635-Agent-Status-and-Information) and look for `reboot_required` under the Checks section:

```
  Checks
  ======
    [...]

    reboot_required 
    -------
      - instance #0 [OK]
      - Collected 0 metrics, 0 events & 1 service check

    [...]
```

## Compatibility

The reboot_required check is currently only compatible with Linux systems.

## Data Collected

### Metrics

No metrics are collected at this time.

### Events

The reboot_required check does not include any events at this time.

## Service Checks

To create alert conditions on these service checks in Datadog, select 'System' on the [Create Monitor](https://app.datadoghq.com/monitors#/create) page, not 'Integration'.

**`system.reboot_required`**:

The check returns:

* `OK` if the system does not require a reboot or for less than `days_warning` or `days_critical`.
* `WARNING` if the system has required a reboot for longer than `days_warning` days.
* `CRITICAL` if the system has required a reboot for longer than `days_critical` days.
