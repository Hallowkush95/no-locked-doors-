# AMD Adrenalin Drivers Bug

* [Temporary Workaround](#workaround)
* [Short explanation](#short-version)
* [Long explanation](#long-version)

There is currently an issue in the new AMD Adrenalin drivers (17.12.1+) that makes them incompatible with NHML. AMD is aware of the bug and hopefully there is a new version that fixes it soon.

Note that some of the miner programs are also affected by this bug. Because of this it is strongly recommended to **not** update to the Adrenalin drivers for the time being.

### Short version
A certain value that is normally returned by the drivers is no longer returned properly. This value is required for NHML to function.

Using NHML with these drivers will cause it to fallback on device mapping and have the following drawbacks:
* Previous benchmark data will not be populated
  * The files are not lost, and benchmark data will return if you install a driver without the bug
  * New benchmark files for each GPU with fallback IDs are generated. You can copy your previous speeds from the proper files as a workaround without changing drivers. When you open the new files there will be a GPU name to identify which GPU they are for.
* Rig stats monitoring will not function
* Certain miners may not function or index properly (e.g. Claymore miners)

### Long version
For a little more technical insight into what is going on:

NHML queries the OpenCL libraries to get specific information on AMD GPUs. In a functioning driver, this query returns the PCIe bus ID for each GPU, however in the Adrenalin drivers a bus ID of 0 is always returned. If you only have one GPU and it *is* on bus ID 0, then you would not see any issues.

This bus ID is necessary to query the AMD Display Library (ADL), which NHML also requires information from. Because bus IDs are not actually being returned, NHML cannot query the ADL to get information like temperature/usage, UUID, PCIe location, etc. NHML uses this information for rig stats monitoring, uniquely identifying GPUs for benchmark data, and the bus ID is used to tell some miners which GPU to mine on (e.g. Claymore). 

Some users with single GPUs have been able to get around this problem by modifying `AMDOpenCLDeviceDetection.exe` so it always returns the bus ID their GPU is on. The problem with this is that a version of `AMDOpenCLDeviceDetextion.exe` needs to be created for specific users, and it does not help users with multiple GPUs.

### Workaround
In 1.8.1.6 there is a new config option you can use to manually specify bus IDs. You can get the bus ID from the device manager properties for your GPU. This method is intended for advanced users and the general recommendation is to not upgrade to Adrenalin drivers for now.

If you have one GPU: Simply edit `configs\General.json` and change the field `OverrideAMDBusIds` from `""` to `"<your bus ID>"`. E.g. if your bus ID is 2, enter `"2"`. (Keep quotations).

If you have more than one GPU, you can add multiple entries separated with commas. E.g. if you have 2 GPUs with IDs 1 and 2, enter `"1,2"`. Note the ordering is important, and it will take some trial and error on your part to find the correct ordering (the ordering is based off of OpenCL indexing that non-Claymore miners use in general).

Note this is not a perfect workaround, as miners need to be updated also to reflect the changes. ClaymoreDual has been updated to 10.3 which supports Adrenalin, however some other Claymore miners still need to be updated and for now will not always mine on correct GPUs. If you have multiple GPUs you will likely need to disable these miners to get optimal performance for now.

