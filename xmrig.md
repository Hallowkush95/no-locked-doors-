# xmrig

| GPU support | Algorithm support | Third party? | Devfee |
|:------------|:------------------|:-------------|--------:
| CPU only | CryptoNightV7 | No |  |

`xmrig` is a CPU miner for CNV7.

For optimal performance see [Locked\Huge Pages](https://github.com/nicehash/NiceHashMinerLegacy/wiki/Notes-and-Hints-on-CPU-Mining#lockedhuge-pages).

## Intensity

Intensity can be adjusted with the thread count `--threads=` ELP.

## Extra Launch Parameters

| Long Name | Short Name | Default | Present if default | Notes |
|:----------|:-----------|--------:|-------------------:|:------|
|`--donate-level=`| | `0` | |
|`--threads=`| `-t` | None| | The optimal value for this is automatically set by xmrig |
|`--av=` | `-v` | `0` | | The optimal value for this is automatically set by xmrig |
|`--cpu-affinity` | | None | |
|`--cpu-priority` | | None | |
|`--no-huge-pages` | | Off | | See [Locked\Huge Pages](https://github.com/nicehash/NiceHashMinerLegacy/wiki/Notes-and-Hints-on-CPU-Mining#lockedhuge-pages) |
|`--no-color` | | Off | |
|`--max-cpu-usage=`| | 75 | |
|`--safe` | | Off | |
