When starting **NiceHash Miner Legacy** (or higher) there will be a file in **MinerReservedPorts.json** in the **configs** folder. From this file you can set what ports to reserve for certain miners and algorithms. If the reserved port is available NiceHash Miner will use the desired port (or ports if there are more) in case the reserved port is unavailable it will fallback and choose one of the available ports starting from **ApiBindPortPoolStart** (default starting 4000 can be set from **General.json** in the **configs** folder). You can reserve more than one port per miner and algorithm (e.g. ethminer has AMD and NVIDIA support and for multi NVIDIA and AMD setup reserve at least two).

Example:

```JSON
{
  "cpuminer": {
    "bin\\cpuminer_opt_AVX2_AES.exe": {
      "Lyra2RE": [],
      "Hodl": [],
      "CryptoNight": []
    },
    "bin\\cpuminer_opt_AVX2.exe": {
      "Lyra2RE": [],
      "Hodl": [],
      "CryptoNight": []
    },
    "bin\\cpuminer_opt_AVX_AES.exe": {
      "Lyra2RE": [],
      "Hodl": [],
      "CryptoNight": []
    },
    "bin\\cpuminer_opt_AVX.exe": {
      "Lyra2RE": [],
      "Hodl": [],
      "CryptoNight": []
    },
    "bin\\cpuminer_opt_AES.exe": {
      "Lyra2RE": [],
      "Hodl": [],
      "CryptoNight": []
    },
    "bin\\cpuminer_opt_SSE2.exe": {
      "Lyra2RE": [],
      "Hodl": [],
      "CryptoNight": []
    }
  },
  "ccminer": {
    "bin\\ccminer_decred.exe": {
      "Decred": []
    },
    "bin\\ccminer_tpruvot.exe": {
      "Lbry": []
    },
    "bin\\ccminer_cryptonight.exe": {
      "CryptoNight": []
    },
    "bin\\ccminer_neoscrypt.exe": {
      "NeoScrypt": []
    },
    "bin\\ccminer_nanashi.exe": {
      "Lyra2REv2": []
    }
  },
  "sgminer": {
    "bin\\sgminer-5-6-0-general\\sgminer.exe": {
      "NeoScrypt": [],
      "Lyra2REv2": [],
      "Decred": [],
      "Lbry": [],
      "Pascal": []
    },
    "bin\\sgminer-5-1-0-optimized\\sgminer.exe": {
      "Lyra2REv2": []
    },
    "bin\\sgminer-gm\\sgminer.exe": {
      "DaggerHashimoto": [],
      "CryptoNight": []
    }
  },
  "nheqminer": {
    "bin\\nheqminer_v0.4b\\nheqminer.exe": {
      "Equihash": []
    }
  },
  "eqm": {
    "bin\\eqm\\eqm.exe": {
      "Equihash": []
    }
  },
  "ethminer": {
    "bin\\ethminer.exe": {
      "DaggerHashimoto": [4001, 4002]
    }
  },
  "ClaymoreAMD": {
    "bin_3rdparty\\claymore_cryptonight\\NsGpuCNMiner.exe": {
      "CryptoNight": []
    },
    "bin_3rdparty\\claymore_zcash\\ZecMiner64.exe": {
      "Equihash": [4003, 4004, 4005]
    }
  },
  "OptiminerAMD": {
    "bin_3rdparty\\optiminer_zcash_win\\Optiminer.exe": {
      "Equihash": [4006, 4058]
    }
  },
  "excavator": {
    "bin\\excavator\\excavator.exe": {
      "Pascal": []
    }
  }
}
```

In the above example ethminer has ports 4001 and 4002 reserved for DaggerHashimoto, Claymore's ZecMiner64 has 4003, 4004 and 4005 has reserved for Equihash and Optiminer (OptiminerZcash) has 4006 and 4058 ports reserved for Equihash. All other miners will use a random available port starting from **ApiBindPortPoolStart**.