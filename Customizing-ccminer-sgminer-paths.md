# Customizing ccminer/sgminer Paths

Starting with NHML 1.8.1.3, the ccminer paths used for NVIDIA and sgminer for AMD mining can be customized. There are some things to note for this:

* Miner paths are decided with two factors:
  * The family of device (e.g. Maxwell, Pascal)
  * The algorithm (e.g. Skunk, X11Gost)
* Editing the path files does not allow adding/removing algorithms on device families. NHML already has this info, the path files are used only once the mining actually begins and it needs to know which ccminer.exe/sgminer.exe to launch.
  * In effect there will be no visual change in NHML that the path files have been customized.
* The paths are relative to the NHML directory, changing to an external folder will not work.
* **Not all miner forks have the same interface or support the same algorithms**. This means sometimes changing the path can cause some features such as benchmarking or speed display to not work correctly, or it may not launch at all. Because of this it is recommended to only change the path once you have tested a different fork outside of NHML and found it to work better.

## Editing the files

After launching NHML 1.8.1.3 for the first time, the `internals` folder will contain new JSON files prefixed with `MinerPathPackage`. The files represent device families. To discern which family you want to edit, read [Finding device family](#devicefam). The files will contain a list of the available algorithms you can edit the paths for.

### Detailed description of MinerPathPackage file contents:

* **Name**: Friendly name for device family (not used for anything else)
* **DeviceType**: Internal ID number NHML uses to identify device (**do not edit**)
* **MinerTypes**: List of base miner types (currently only one in each device family), each containing:
  * **Name**: Friendly name for miner type (not used for anything else)
  * **Type**: Internal ID number NHML uses to identify miner type (**do not edit**)
  * **Algorithms**: List of algorithms supported on this miner type, each containing:
    * **Name**: Friendly name for algorithm (not used for anything else)
    * **Algorithm**: Internal ID number NHML uses to identify algorithm (**do not edit**)
    * **Path**: Miner path to use for this algorithm, relative to NHML main directory (the one with `NiceHashMinerLegacy.exe`). **This is the only field that should be edited**. It is recommended to only change the folder that comes after `bin`, but you are able to put in a path to any folder within the NHML directory. Make sure to use double slashes instead of the single that is normally used in Windows.

### <a name="#devicefam"></a>Finding device family

Device families are the following:

* **AMDOpenCL**: All AMD GPUs
* **NVIDIA_2_1**: Most Fermi devices (most of 400/500 series)
* **NVIDIA_3_x**: All Kepler devices (most of 600/700 series)
* **NVIDIA_5_x**: All Maxwell devices (all of 900 series, 750 Ti)
* **NVIDIA_6_x**: All Pascal devices (all of 1000 series)

The number for NVIDIA families is the GPU's *CUDA Compute Capability*. You can find a full list of which NVIDIA devices are included in which CC level on [Wikipedia](https://en.wikipedia.org/wiki/CUDA#GPUs_supported). Most of the exceptions to the series listed above are mobile cards.