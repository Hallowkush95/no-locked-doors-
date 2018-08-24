# ccminer

`ccminer` is the main miner used for NVIDIA and works with a large variety of algorithms. There are many different forks included, each of which is tuned for better performance under certain conditions. The fork used when mining depends on which algorithm and device generation is used. 

## Extra Launch Parameters

| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
|`--intensity`|`-i` | `0` | 

### Additionally the CryptoNight fork supports
| Long Name | Short Name | Default | Present if default |
|:----------|:-----------|--------:|-------------------:|
|`--launch=` | `-l` | `8x40` |
| `--bfactor=` | | `0` | 
| `--bsleep=` | | `0` | 