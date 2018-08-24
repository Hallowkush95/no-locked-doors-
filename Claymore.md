# Claymore

Three Claymore miners are included with NHML as optional third-party miners:

* [`ClaymoreZcash`]()
* [`ClaymoreCryptoNote`]()
* [`ClaymoreDual`]()

## Common Extra Launch Parameters

All Claymore miners support the following ELPs, as well as version-specific ones listed on their pages.

| Long Name | Short Name | Default | Present if default | Temperature Control |
|:----------|:-----------|--------:|-------------------:|----------------------------------------------:|
| | `-tt` | None | | Yes |
| | `-tstop` | None | | Yes |
| | `-fanmax` | None | | Yes |
| | `-fanmin` | None | | Yes |
| | `-nofee` | Off | |
| | `-wd` | `1` | |
| | `-li` | Off | |
| | `-cclock` | None | |
| | `-mclock` | None | |
| | `-powlim` | None | |
| | `-cvddc` | None | |
| | `-mvddc` | None | |