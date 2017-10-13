# Algorithm ExtraLaunchParameters
## How does it work:
If you are an advanced user that wants to tweak the performance of your GPUs or CPUs you can set **supported** options in the **ExtraLaunchParameters** for selected Device and Algorithm.

If you have 3 AMD devices with the following **ExtraLaunchParameters** settings for algorithm A and B:
  - **device1** --xintensity 1024 --worksize 64 --gputhreads 2
  - **device2** --xintensity 512 --worksize 128 --gputhreads 2
  - **device3** --xintensity 512 --worksize 64 --gputhreads 4

If **algorithm A** is most profitable for device1 and device2 and **algorithm B** for device3, NiceHashMiner will run two sgminers for A and B like so:
  - sgminer .. --xintensity 1024,512 --worksize 64,128 --gputhreads 2,2 .. (device1 and device2)
  - sgminer .. --xintensity 512 --worksize 64 --gputhreads 4 .. (device3)

If **algorithm A** is most profitable for all three devices, NiceHashMiner will run two sgminers for A like so:
  - sgminer .. --xintensity 1024,512,512 --worksize 64,128,64 --gputhreads 2,2,4 .. (device1, device2, device3)

So when setting **ExtraLaunchParameters** set them **per device and algorithm** NiceHashMiner will group them accordingly.
If you leave **ExtraLaunchParameters** empty the defaults will be used or ignored if no parameters have been set.

# Supported options
## NVIDIA Miners

### ccminers
| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
|`--intensity`|`-i` | `0` | 

### ccminer CryptoNight (extra over NVIDIA ccminers)
| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
|`--launch=` | `-l` | `8x40` |
| `--bfactor=` | | `0` | 
| `--bsleep=` | | `0` | 

### ethminer DaggerHashimoto
| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
|`--cuda-block-size` | | `128` | 
|`--cuda-grid-size` | | `8192` | 

### excavator (Equihash and Pascal)
| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
| | `-c1` | `0` |
| | `-c2` | `0` | 
| | `-ct` | `1` for Pascal; `2` for Equihash |

### EWBF Equihash
| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
| `--fee` | | `0` | Yes |
| `--templimit` | | `90` | 
| `--tempuinits` | | `C` |
| `--eexit` | | None | 
| `--solver | | `0` |
| `--intensity | | `64` |
| `--pec` | | Off | 

## AMD Miners

### sgminer
| Long Name | Short Name | Default | Present if default | Temperature Control | Notes |
|:----------|:-----------|--------:|-------------------:|--------------------:|:------|
|`--keccak-unroll` | | `0` |  | |
|`--hamsi-expand-big` | | `4` |  | |
|`--nfactor` | | `10` | | |
|`--intensity` | `-I` | `d` | | |
|`--xintensity` | `-X` | `-1` |  | | Overrides `--intensity` |
|`--rawintensity` | | `-1` |  | | Overrides `--xintensity` |
|`--thread-concurrency` | | `-1` |  | |
|`--worksize` | `-w` | `-1` | |
|`--gpu-threads` | `-g` | `-1` |  |
|`--lookup-gap` | | `-1` | |
|`--remove-disabled` | | On | Yes |
|`--gpu-fan`| | `30`-`60` |  | Yes |
|`--temp-cutoff` | | `95` | | Yes |
|`--temp-overheat` | | `85` |  | Yes |
|`--temp-target` | | `75` | | Yes |
|`--auto-fan` | | Off | | Yes |
|`--auto-gpu` | | Off | | Yes |

### ClaymoreZcash Equihash

| Long Name | Short Name | Default | Present if default | Temperature Control |
|:----------|:-----------|--------:|-------------------:|----------------------------------------------:|
| | `-a` | `0` | |
| | `-asm` | `1` | |
| | `-i` | `4` |  |
| | `-ttli` | None || Yes |

### Claymore CryptoNight
| Long Name | Short Name | Default | Present if default | Temperature Control |
|:----------|:-----------|--------:|-------------------:|--------------------:|
| | `-a` | `0` |  |
| | `-h` | `0` | |

### OptiminerZcash
| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
| `--force-generic-kernel` | | Off | 
| `--experimental-kernel` | | Off |
| `--nodevfee` | | Off | 
| | `-i` | None | 
| `--pci-mode` | | None |

## NVIDIA and AMD Miners

### ClaymoreDual
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
| | `-dcri` | `30` | | | | See [Tweaking ClaymoreDual Intensity](https://github.com/nicehash/NiceHashMinerLegacy/wiki/Tweaking-ClaymoreDual-Intensity) |
| | `-dcrt` | `5` | |
| | `-ttdcr` | None | | Yes |
| | `-ttli` | None | | Yes |

### Common Claymore Miner Options

| Long Name | Short Name | Default | Present if default | Temperature Control |
|:----------|:-----------|--------:|-------------------:|----------------------------------------------:|
| | `-tt` | None | | Yes |
| | `-tstop` | None | | Yes |
| | `-fanmax` | None | | Yes |
| | `-fanmin` | None | | Yes |
| | `-nofee` | Off | |
| | `-wd` | `1` | |
| | `-li` | Off | |
| | `-cclock` | None | |
| | `-mclock` | None | |
| | `-powlim` | None | |
| | `-cvddc` | None | |
| | `-mvddc` | None | |


## CPU Miners

### xmrig
| Long Name | Short Name | Default | Present if default | Notes |
|:----------|:-----------|--------:|-------------------:|:------|
|`--donate-level=`| | `0` | |
|`--threads=`| `-t` | None| |
|`--av=` | `-v` | `0` | |
|`--cpu-affinity` | | None | |
|`--cpu-priority` | | None | |
|`--no-huge-pages` | | Off | | See Huge Pages |
|`--no-color` | | Off | |
|`--max-cpu-usage=`| | 75 | |
|`--safe` | | Off | |


# How to add missing miner flag
You can now add missing miner flags for certain miners (when manually updating/changing miners). After first start of **NiceHash Miner (v1.7.4.4 and up)** there will be an **internals** folder created. Here you will see **MinerOptionPackage_'MINER NAME'.json**. If there is a missing parameter you can edit the **GeneralOptions** for general optimizations or **TemperatureOptions** for temperature settings. This is the ccminer default:

```JSON
{
  "Name": "ccminer",
  "Type": 1,
  "GeneralOptions": [
    {
      "Type": "Intensity",
      "ShortName": "-i",
      "LongName": "--intensity=",
      "Default": "0",
      "FlagType": 2,
      "Separator": ","
    }
  ],
  "TemperatureOptions": []
}
```

There is only one general option **Intensity**. It has a short parameter name (**ShortName**), long parameter name (**LongName**), default value _**Please NOTE that this is the IgnoreDefaultValue. It will not set the miners to the set value, this value is for the parser to ignore**_ (**Default**), FlagType of 2 = MultiParam  ([explanation](https://github.com/nicehash/NiceHashMiner/wiki/Algorithm-ExtraLaunchParameters#flagtype) ) and a comma separator (**Separator**).

## FlagType 
This parameter indicates how to group multiple devices:
 - **Uni = 0** this means that the flag doesn't have any parameters 
 - **SingleParam = 1** this means that the flag has only one parameter
 - **MultiParam = 2**  this means that the flag accepts more than one parameter (example two gpus with different intensity values)
 - **DuplicateMultiParam = 3** flag repeats per device (this is for OptiminerZcash intensity only)