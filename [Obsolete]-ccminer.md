# ccminer

`ccminer` is the main miner used for NVIDIA and works with a large variety of algorithms. There are many different forks included, each of which is tuned for better performance under certain conditions. The fork used when mining depends on which algorithm and device generation is used. 

## Intensity

Intensity for `ccminer` can be adjusted by setting the `--intensity` ELP. The default is "auto-select", which occurs when a value of `0` is passed. This generally selects an intensity of around 20 depending on the performance of the GPU. When looking to use less GPU resources, start around there and adjust downward.

## Extra Launch Parameters

| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
|`--intensity`|`-i` | `0` | 

Additionally the CryptoNight fork supports:

| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
|`--launch=` | `-l` | `8x40` |
| `--bfactor=` | | `0` | 
| `--bsleep=` | | `0` | 