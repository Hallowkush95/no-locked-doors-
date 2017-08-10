# Rig Stats Monitoring

## Supported devices

There are 4 metrics available to monitor:

* Device name/enabled status: Shows the name of the device and whether or not it is enabled in NHML
* Load: Percentage of usage 
* Fan speed: Speed of fan in RPMs
* Temperature: Temperature of device in Celsius 

Not all metrics are supported by every device. If one is not supported or there is an error, it will report as `0`.

| Device Type | Enabled status | Load | Fan Speed | Temperature |
|:------------|---------------:|-----:|----------:|------------:|
| CPU         | Yes            | Yes  | No        | No          |
| NVIDIA GPU  | Yes            | Yes  | Yes       | Yes         |
| AMD GPU     | Yes            | Yes  | Yes       | Yes         |

## Getting Started

1. Make or login to an account at https://new.nicehash.com/
2. Use the Bitcoin address created with your account to mine on NHML
3. Whether or not you are mining, NHML will upload the statistics every minute
4. You can view the statistics on your mining details page, https://new.nicehash.com/miner/<btcaddress> where <btcaddress> is your Bitcoin address. You may also click the "Check my stats online!" link on the NHML window
5. On the page, as long as you are still logged into the account associated with the BTC address, you can scroll down to "Rig Stats" and expand workers to view device stats

## Troubleshooting

The most common cause of misreported statuses are improper driver installations. Before going further, try reinstalling your drivers.

If you are not seeing certain metrics on the Rig Stats page but they should be supported, there may be errors shown in your `\logs\log.txt` file. You can open an issue and post your `log.txt` and someone will try to track down the problem with you.