# ethminer

| GPU support | Algorithm support | Third party? | 
|:------------|:------------------|:-------------|
| All ethereum-capable NVIDIA | DaggerHashimoto (ethash) | No |

`ethminer` is a NVIDIA only miner for DaggerHashimoto. It is largely superseded by `claymore_dual` but is kept as an open-source alternative.

## Intensity

Intensity may be adjusted by tweaking both ELPs.

## Extra Launch Parameters

| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
|`--cuda-block-size` | | `128` | 
|`--cuda-grid-size` | | `8192` | 
