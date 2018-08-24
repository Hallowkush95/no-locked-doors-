# sgminer

| GPU support | Algorithm support | Third party? | Devfee |
|:------------|:------------------|:-------------|--------:
| All AMD | Many | No |  |

`sgminer` is an OpenCL miner used for various algorithms on AMD cards. Not all algorithms are available on all AMD devices. 

`sgminer` is known to cause BSOD issues when running over a remote connection, particularly RDP. If experiencing crashes over a remote connection, it is recommended to try with `sgminer` disabled.

## Intensity

Three different ELPs can be used to adjust intensity: `--intensity`, `--xintensity`, and `--rawintensity`. They express the same setting, but with different numbers. When more than one is present, only one will be used.

## Extra Launch Parameters

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
