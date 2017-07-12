# Contents

* [Installing](#installing)
* [Upgrading](#upgrading)
* [Advanced Algorithms](#advancedalgos)
* [Manual Benchmarking](#manualbenchmarking)

## <a name="installing"></a> Installing

1. Grab the [latest release zip file](https://github.com/DillonN/NiceHashMiner/releases/latest) and unzip the folder to a place of your choosing, then run `NiceHashMiner.exe`.

2. When running NHM for the first time it will automatically download the miner bins. Due to a bad connection to GitHub, some users may find that NHM gets stuck on the downloading process. If it is stuck for longer than ~20s, kill NiceHashMiner and try again. Alternatively, you can download the bin .zip files (`bin.zip` and `bin_3rdparty.zip` if you consented to 3rd party miners) from the release page. Simply extract the contained folders `bin` and `bin_3rdparty` to the same directory as `NiceHashMiner.exe`.

3. Once NHM is loaded, enter your Bitcoin address and workername (0-7 characters, letters/numbers only) then run through the benchmark. NHM will automatically go through all enabled algorithm/miner combinations and record their speeds. If some fail, you can try them again with time set to "Precise".

4. If you are unable to get a benchmark to run, follow [Manual Benchmark](#manualbenchmarking) instructions.

5. Once you are satisfied with the benchmarked algorithms, close the benchmark window and click start. NHM will automatically start the most profitable miner/algorithm combination based on the current paying rates from NiceHash.

6. That's it! Let it run, and NHM will frequently check the NiceHash rates and switch to the most profitable miner. You can set a delay on the switching in settings.

## <a name="upgrading"></a> Upgrading

The recommended method of upgrading is to extract the new .zip into a new folder, and only copy over your config files. The config files are located in the `configs` folder, so just drag that folder to the new directory.

You can usually get away with just deleting the bin and bin_3rdparty folders, and then overwriting the remaining files. When you re-launch NiceHash, it will download the correct bin files automatically.

If you don't delete the folders, it will often leave NiceHash in an inconsistent state causing various issues:

* Not deleting the bin folders will lead to not getting any miner updates. 
* Any added "Extra Launch Options" will not work. These are cached in the `internals` folder, so you can safely delete this folder and NHM will reconstruct it. 

If you don't care about whatever miner updates there may be and hate waiting for the download, you can keep your bin folders. There will still be an auto-download if a brand new miner has been added.

## <a name="advancedalgos"></a> Advanced Algorithms

Some algorithms are geared more toward advanced users because they require more care and/or are experimental. These will be disabled by default in the benchmark section. 

There is nothing wrong with enabling the disabled algorithms, and they are generally more profitable, but you should be prepared for:

* Terminated benchmarks (can be fixed through [manual benchmarking](#manualbenchmarking)

* Crashes (open an [Issue](https://github.com/DillonN/NiceHashMiner/issues) and post your log files for help)

* Tweaking to get the most profit (e.g. [Dual Algorithm intensity](https://github.com/DillonN/NiceHashMiner/wiki/Tweaking-ClaymoreDual-intensity))

## <a name="manualbenchmarking"></a> Manual Benchmarking

Sometimes you may not be able to benchmark specific algorithms. The following steps will allow you to benchmark them manually (and if the benchmark failure is due to a crash, better pinpoint the problem):

1. Open settings, and make sure `General -> Hide Mining Windows` is unchecked.

2. Go to the `Devices/Algorithms` tab and find the algorithm you wish to benchmark.

3. Disable all algorithms except the one you want to bench (can be done by right clicking and selecting `Disable All Algorithms`). Optionally disable your other devices (recommended if they are the same).

4. Enter any number into the `Benchmark Speed (H/s)` field, then save and close settings.

5. Run the miner and the one you selected should pop up (NOTE: if you have more than one identical card and a different algorithm is popping up, disable your other cards). 

6. Let the miner run long enough to get a stable hashrate. Remember this number, then go back to `Settings -> Devices/Algorithms` and enter it manually in the `Benchmark Speed (H/s)` field. Note miners will generally show hashrates in larger units "e.g. GH/s" so you will have to add zeroes to adjust for this (look at the speed column to see it formatted with larger units).

7. That's it! Once you've saved those settings, NHM will remember the speed you've found and use it for auto-switching.