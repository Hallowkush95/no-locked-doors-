# ClaymoreDual

| GPU support | Algorithm support | Third party? | Devfee |
|:------------|:------------------|:-------------|--------:
| All Ethereum-capable NVIDIA and AMD | DaggerHashimoto + various secondary | Yes | 1.5/1.0% |

`ClaymoreDual` is a unique closed-source miner developed by Claymore. It primarily supports DaggerHashimoto mining, but optionally can be used to mine a secondary coin simultaneously, greatly increasing profits in many scenarios. It is also a very capable Dagger miner on its own when not utilizing the dual option.

## Dual Mining

Dual mining is supported in NHML through the separate `ClaymoreDual` entries in the algorithm list. Each entry shows the secondary coin, as well as primary/secondary hashrates if they have been benchmarked. 

The profits for both primary (Dagger) and secondary algorithms are added together when NHML decides whether or not to switch. 

The following secondary algorithms are supported:

* Blake2s
* Decred
* Pascal
* Keccak
* Lbry
* Sia

When dual mining, the devfee is raised from 1.0% to 1.5% (this is taken into account during benchmarking). 

## Tweaking Dual Intensity

When dual mining, the intensity with which the secondary algo is mined can be adjusted. The right value to use varies wildly depending on the card and algo, and also current prices. Adjustments can be made with the `-dcri` ELP, which has a default value of `30`.

### Tweaking Dual Automatically (new method)

As of 1.9.0.0 NHML supports tweaking `-dcri` automatically. This can be done by right clicking on the dual algorithm entry in the benchmark window, and checking ClaymoreDual Tuning -> Tuning Enabled. That is the only step required to enable automatic tuning of the secondary intensity.

By default, NHML will test values of `dcri` from 25 to 200 in increments of 25. This drastically increases benchmarking time, however with a proper BTC address entered the benchmarks will mine to your account.

The values tuned can be adjusted by clicking ClaymoreDual Tuning -> Tuning Settings. This will open up a window showing all benchmarked values of `dcri` and their respective hashrates/profitability. With the text boxes on the side, the range and interval for `dcri` values to benchmark can be changed.

Once the tuning is over, NHML will have stored the hashrates for every value it benchmarked. As the prices for Dagger and the secondary algo fluctuate, it will select the `dcri` value with the most profit.

### Tweaking Dual Intensity Manually (old method)

#### Saving a value

1. Open settings, then go to the "Devices/Algorithms" tab. Select the dual algo you wish to save for, and put in `-dcri <your number>` e.g. `-dcri 150`.

2. Update "Benchmark Speed" and "Secondary Benchmark Speed" with the hashrates you found. Alternatively, you can rerun the benchmark by right clicking on the algo and selecting "Clear Algorithm Speed" and running the benchmark as normal.

#### Tweaking a value

1. Uncheck hide miners in settings and start mining with the dual algo you want to tweak (e.g. DaggerSia)

2. While mining, highlight the miner window and hit + or - on your keyboard. You will see a message come up "-dcri set to ##". Keep playing with that value and watch the NHM window to see if your profit goes up or down. 

3. Once you've found the right number, save it as per the previous section.

## Extra Launch Parameters

As well as the [common Claymore ELPs](https://github.com/nicehash/NiceHashMinerLegacy/wiki/Claymore#common-extra-launch-parameters), `ClaymoreDual` supports the following:

| Long Name | Short Name | Default | Present if default | Temperature Control | Controlled by DualMining | Notes |
|:----------|:-----------|--------:|-------------------:|--------------------:|-------------------------:|:------|
| | `-etha` | `-1` |  |
| | `-ethi` | `8` |  |
| | `-asm` | `1` | |
| | `-i` | `4` | |
| | `-eres` | `2` | |
| | `-erate` | `1` | |
| | `-estale` | `1` | |
| | `-gser` | `0` |  |
| | `-retrydelay` | `20` ||
| | `-lidag` | `0` |  |
| | `-etht` | `200` |  |
| | `-allcoins` | On | Yes |
| | `-r` | `0` |  |
| | `-ftime` | `0` | |
| | `-mode` | `0` |  | | Yes |
| | `-dpool` | None |  | | Yes |
| | `-dwal` | None |  | | Yes |
| | `-dpsw` | None |  | | Yes |
| | `-dcoin` | None |  | | Yes |
| | `-dcri` | `30` | | | | See previous section |
| | `-dcrt` | `5` | |
| | `-ttdcr` | None | | Yes |
| | `-ttli` | None | | Yes |