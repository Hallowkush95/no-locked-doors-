In order for some miners to work correctly (mostly AMD miners) specific Environment Variables need to be set.
NiceHash Miner will set these variables by default under **\\configs\\MinerSystemVariables.json** file. If one needs to change or add additional Environment Variables it can be done by setting the miner path and environment name value pairs.

Example: 
```CS
{
  "bin_3rdparty\\claymore_dual\\EthDcrMiner64.exe": // miner path
  // key value pairs => "Name" : "Value"
  {
    "GPU_MAX_ALLOC_PERCENT": "100",
    "GPU_USE_SYNC_OBJECTS": "1",
    "GPU_SINGLE_ALLOC_PERCENT": "100",
    "GPU_MAX_HEAP_SIZE": "100",
    "GPU_FORCE_64BIT_PTR": "0"
  }
}