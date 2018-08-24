# Algorithm Extra Launch Parameters (ELPs)

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

## Supported options

See the miner's page under [list of miners](https://github.com/nicehash/NiceHashMinerLegacy/wiki/Miners#list-of-included-miners).

## How to add missing miner flags

You can add missing miner flags for certain miners (when manually updating/changing miners). After first start of **NiceHash Miner (v1.7.4.4 and up)** there will be an **internals** folder created. Here you will see **MinerOptionPackage_'MINER NAME'.json**. If there is a missing parameter you can edit the **GeneralOptions** for general optimizations or **TemperatureOptions** for temperature settings. This is the ccminer default:

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