---
title: Licensing
summary: Outlines license usage, management, and restrictions
component: core
reviewed: 2017-08-15
redirects:
 - nservicebus/licensing-limitations
 - nservicebus/licensing/licensing-limitations
 - nservicebus/licensing/license-management
 - nservicebus/license-management
related:
 - nservicebus/upgrades/release-policy
 - nservicebus/upgrades/support-policy
 - servicecontrol/license
 - serviceinsight/license
---


## License details

See the [Licensing page](https://particular.net/licensing) for license specifics.

## Validation license

License information is logged when an endpoint instance is started.

### NServiceBus 3

No license:
```
2018-01-12 17:35:47,823 [1] INFO  NServiceBus.Licensing.LicenseManager [(null)] <(null)> - No valid license found.
2018-01-12 17:35:47,825 [1] DEBUG NServiceBus.Licensing.LicenseManager [(null)] <(null)> - Trial for NServiceBus v3.3 is still active, trial expires on 26-1-2018.
2018-01-12 17:35:47,827 [1] INFO  NServiceBus.Licensing.LicenseManager [(null)] <(null)> - Configuring NServiceBus to run in trial mode.
```

Correct license:
No log entries written by NServiceBus 3.

### NServiceBus 4

With License
```
2018-01-12 17:44:40,861 [1] INFO  NServiceBus.Licensing.LicenseManager [(null)] <(null)> - UpgradeProtectionExpiration: 02/23/2019 00:00:00
```


Expired trial license
```
2018-01-12 17:48:58,863 [1] WARN  NServiceBus.Licensing.LicenseManager [(null)] <(null)> - Trial for the Particular Service Platform has expired
```

## License validity

partial: validity


## Throughput limitations

partial: limitations


## License management

There are several options available for installing the license file. 

partial: license-management


## Troubleshooting

### Failed to initialize the license

The license management code requires write permissions to store metadata. If the process credentials don't have write permissions the following fatal event log item can be generated:

```
FATAL NServiceBus.Features.LicenseReminder Failed to initialize the license
System.UnauthorizedAccessException: Access to the path 'C:\Windows\system32\config\systemprofile' is denied.
```

Ensure that the process has write permissions at the specified location. If necessary, either modify the location, change permissions, or use another process that has appropriate permissions.
