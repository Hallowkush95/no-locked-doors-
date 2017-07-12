Check here first, then open an [Issue](https://github.com/NiceHash/NiceHashMinerLegacy/issues) if you still need help (also search for your issue to see if it has been posted before). Provide log files.

* [Missing .dll errors](#dllerrors)
* [Benchmark won't complete](#bench)
* [NiceHashMiner is making Windows laggy](#lag)
* [Freezing/Display driver crashing while mining](#ddcrash)
* [Discrepancy between NiceHashMiner reported hashrates and NiceHash online stats](#profitdisc) 
* [No supported devices](#nosupportdev)

### <a name="dllerrors"></a> Missing .dll errors

These errors are generally caused because you don't have the correct version of Microsoft Visual C++ Redistributable installed. Users who use their computer as a daily driver will likely not run into this issue since VC++ is required for a great number of other programs.

An effort is made to include the correct .dlls, however sometimes this may slip through. If you run into this issue while opening a specific miner, try to find the specific .dll file in the NiceHashMiner directory, then copy it to the directory for the miner giving you issues. You can also open an [Issue](https://github.com/NiceHash/NiceHashMinerLegacy/issues) and on the next bin file update, I will add in the correct .dll.

Alternatively, you can install one of the Redistributables from Microsoft and every program will work without the need for copying .dlls since your Windows will have it (not just for NiceHashMiner, but any other programs as well). This will solve issues if the required .dll is of the form `msvcr<version>.dll` or `msvcp<version>.dll`. For each, try the x64 install first.

* If `<version> = 120` [VC++ 2013](https://www.microsoft.com/en-ca/download/details.aspx?id=40784)

* If `<version> = 140` Run the VC++ 2015 installer in the `bin` folder, `vc_redist.x64.exe`

* If `<version> = 141` [VC++ 2017](https://go.microsoft.com/fwlink/?LinkId=746572)

### <a name="bench"></a> Benchmark won't complete

First, try running the benchmark on "Precise". If it still doesn't complete, [manually benchmark](https://github.com/NiceHash/NiceHashMinerLegacy/wiki/Getting-started#manualbenchmarking) the troublesome algorithm.

### <a name="lag"></a> NiceHash Miner Legacy is making Windows laggy

On a dedicated mining box, if the processor and motherboard support integrated graphics, simply connect the monitor to that instead. Otherwise, you could try decreasing the intensity for the miner that is causing problems, and accepting that it will run at a slightly slower speed. Google the file name of the miner and find a command line option to do with 'intensity'. Add this to the extra launch options for this miner, probably using a smaller number until it works better.
* example 1: For claymore dual miners something like "-ethi 3" will probably help.
* example 2: sgminer's algorithms usually support an "--intensity ##" or "--xintensity ##" setting.

A dedicated page on this is coming soon.

### <a name="ddcrash"></a> Freezing/display driver crashing while mining

Try disabling overclock if you have one. If not, this is usually caused by a conflict of the miner and your drivers, try opening an [Issue](https://github.com/NiceHash/NiceHashMinerLegacy/issues).

### <a name="profitdisc"></a> Discrepancy between NiceHash Miner Legacy reported hashrates and NiceHash online stats

These discrepancies are normal and can be caused by fluctuations in the NiceHash network. The important value to check on the NiceHash online stats is the profit that is averaged over the last hour (in the box with projected monthly/weekly/daily profits). The fluctuations are more or less noise and can go up and down, canceling each other out over time.

If your displayed profit is much lower than expected, make sure you aren't getting rejected shares which can be caused by overclocks/poor network connection.

[Official comment](https://www.reddit.com/r/NiceHash/comments/6in4aw/mining_the_speed_on_the_web_is_not_the_same_as/)

### <a name="nosupportdev"></a> No supported devices

You will get a message stating there are no supported devices found if NHML is not able to access any devices on your system. The first thing to check is whether your devices are supported:

* CPUs: must support 64-bit and [AES instruction set](https://en.wikipedia.org/wiki/AES_instruction_set#Intel_and_AMD_x86_architecture). You can look up your specific CPU to make sure it supports this.

* NVIDIA: Cuda Compute Capability 2.1 or higher. This includes *most* GPUs since the GeForce 600 series (and some older ones).

* AMD: Any GPU with OpenCL support (note older GPUs, especially those with little VRAM, may perform poorly).

Also old drivers may not show up in NHML. Try with the latest drivers to see if detection works.

If you are certain your device is supported and it is connected and properly to your computer:

**Users with a Maxwell 2.0 GPU only, meaning:**

* For desktop: all GTX 900 series cards (note this does not include the GT card)

* For mobile: all GTX 900m series cards 965m and up

These GPUs have a setting in the NVIDIA Control Panel (NVCP) called "Optimize for computer performance". This mode can cause NHML to not be able to detect the GPU. Make sure this value is off in global settings. If you need the setting on for a specific program, you can disable it globally and add a program specific rule to enable it.

If you are still unable to get your device to show up, please open an issue *and attach your log file*.