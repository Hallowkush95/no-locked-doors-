# Contents

* [Installing](#installing)
* [Upgrading](#upgrading)
* [Advanced Algorithms](#advancedalgos)
* [Manual Benchmarking](#manualbenchmarking)

## <a name="installing"></a> Installing

1. Grab the [latest release zip file](https://github.com/NiceHash/NiceHashMinerLegacy/releases/latest) and unzip the folder to a place of your choosing, then run `NiceHashMinerLegacy.exe`.

2. When running NHML for the first time it will automatically download the miner bins. Alternatively, you can download the bin .zip files (`bin.zip` and `bin_3rdparty.zip` if you consented to 3rd party miners) from the release page. Simply extract the contained folders `bin` and `bin_3rdparty` to the same directory as `NiceHashMinerLegacy.exe`.

3. Once NHML is loaded, enter your Bitcoin address and workername (0-7 characters, letters/numbers only) then run through the benchmark. NHML will automatically go through all enabled algorithm/miner combinations and record their speeds. If some fail, you can try them again with time set to "Precise".

4. If you are unable to get a benchmark to run, follow [Manual Benchmark](#manualbenchmarking) instructions.

5. Once you are satisfied with the benchmarked algorithms, close the benchmark window and click start. NHML will automatically start the most profitable miner/algorithm combination based on the current paying rates from NiceHash.

6. That's it! Let it run, and NHML will frequently check the NiceHash rates and switch to the most profitable miner. You can set a delay on the switching in settings.

## <a name="upgrading"></a> Upgrading

The recommended method of upgrading:

1. Extract the new .zip into a new folder 
2. Copy the `configs` folder from the old folder to the new one. **Do not** copy over anything else
3. Run the new `NiceHashMinerLegacy.exe` and it will download the updated miner files automatically

If you extract the new zip to overwrite all the files, it will lead NHML to be in an inconsistent state:

* You will not get any miner updates (occasionally this can cause issues if NHML relies on the updated miner)
* Any added "Extra Launch Options" will not work. These are cached in the `internals` folder, so you can safely delete this folder and NHML will reconstruct it. 

## <a name="advancedalgos"></a> Advanced Algorithms

Some algorithms are geared more toward advanced users because they require more care and/or are experimental. These will be disabled by default in the benchmark section. 

There is nothing wrong with enabling the disabled algorithms, and they are generally more profitable, but you should be prepared for:

* Terminated benchmarks (can be fixed through [manual benchmarking](#manualbenchmarking)

* Crashes (open an [Issue](https://github.com/NiceHash/NiceHashMinerLegacy/issues) and post your log files for help)

* Tweaking to get the most profit (e.g. [Dual Algorithm intensity](https://github.com/NiceHash/NiceHashMinerLegacy/wiki/Tweaking-ClaymoreDual-Intensity))

## <a name="manualbenchmarking"></a> Manual Benchmarking

Sometimes you may not be able to benchmark specific algorithms. The following steps will allow you to benchmark them manually (and if the benchmark failure is due to a crash, better pinpoint the problem):

1. Open settings, and make sure `General -> Hide Mining Windows` is unchecked.

2. Go to the `Devices/Algorithms` tab and find the algorithm you wish to benchmark.

3. Right click on the algorithm and click "Enable only this". This will disable all other algorithms. If the algorithm doesn't have a speed, it will be automatically set to 1H/s as a placeholder.

5. Run the miner and the one you selected should pop up (NOTE: if you have more than one identical card and a different algorithm is popping up, disable your other cards). 

6. Let the miner run long enough to get a stable hashrate. Remember this number, then go back to `Settings -> Devices/Algorithms` and enter it manually in the `Benchmark Speed (H/s)` field. Note miners will generally show hashrates in larger units "e.g. GH/s" so you will have to add zeroes to adjust for this (look at the speed column to see it formatted with larger units).

7. Re-enable the other algorithms that were disabled in step 3. Once you've saved those settings, NHML will remember the speed you've found and use it for auto-switching.