The `-dcri` value adjusts how hard the miner works on the second coin, which can potentially eat into the Eth hashrate. For bigger cards like a 1080 Ti there is generally a lot of room to increase dcri without lowering Eth. Profit gains of up to 60% can be obtained on these cards after tweaking. Smaller cards like the 480 probably won't see much benefit, and even smaller cards may get more benefit by decreasing the value.

These values are rough and can fluctuate based on the paying rates of Eth and the secondary coins, so it is best to try out for yourself.

The default value is `-dcri 30` which is usually a good value for cards similar to 290/390/480/580. Instructions on how to adjust yourself at the end.

## Tested values

### NVIDIA

| Card            | Secondary Coin | `−dcri` | Eth Hashrate (MH/s) | Secondary Hashrate (MH/s) |
|:----------------|:---------------|--------:|--------------------:|--------------------------:|
|1080 Ti          | Sia            | 150     | 30.5                | 1550                      |
|                 | Pascal         |  90     | 32.0                |  950                      |
|                 | Lbry           |  80     | 30.0                |   60                      |
| 1080¹           | Sia            | 150     | 22.0                | 1100                      |
|                 | Decred         | 210     | 22.0                | 1540                      |
|                 | Pascal         | 100     | 22.0                |  730                      |
|                 | Lbry           | 160     | 22.0                |   80.5                    |
| 1070&nbsp;FE²   | Sia            |  55     | 28.0                |  515                      |
|                 | Decred         |  80     | 27.0                |  720                      |
|                 | Pascal         |  35     | 27.5                |  320                      |
|                 | Lbry           |  50     | 27.0                |   37.5                    |
| 1060&nbsp;3G³   | Sia            |  55     | 19.0                |  350                      |
|                 | Decred         |  80     | 18.5                |  495                      |
|                 | Pascal         |  40     | 18.5                |  245                      |
|                 | Lbry           |  30     | 19.0                |   18.5                    |
| 980             | Sia            |  55     | 17.0                |  340                      |
|                 | Decred         |  55     | 15.5                |  280                      |
|                 | Pascal         |  60     | 16.5                |  275                      |
|                 | Lbry           |  45     | 17.5                |   22.5                    |

¹) Core +150, Mem +450, PL 85%
²) Core +200, Mem +600, PL 85%
³) Core    0, Mem +500, PL 90%

### AMD

| Card            | Secondary Coin | `-dcri` | Eth Hashrate (MH/s) | Secondary Hashrate (MH/s) |
|:----------------|:---------------|--------:|--------------------:|--------------------------:|
|Fury X           |SIA             | 40      | 30.5                | 1200                      |
|290X             |SIA             | 27      | 29                  | 800                       |

## Instructions

### Saving a value

1. Open settings, then go to the "Devices/Algorithms" tab. Select the dual algo you wish to save for, and put in `-dcri <your number>` e.g. `-dcri 150`.

2. Update "Benchmark Speed" and "Secondary Benchmark Speed" with the hashrates you found. Alternatively, you can rerun the benchmark by right clicking on the algo and selecting "Clear Algorithm Speed" and running the benchmark as normal.

### Tweaking a value

1. Uncheck hide miners in settings and start mining with the dual algo you want to tweak (e.g. DaggerSia)

2. While mining, highlight the miner window and hit + or - on your keyboard. You will see a message come up "-dcri set to ##". Keep playing with that value and watch the NHM window to see if your profit goes up or down. 

3. Once you've found the right number, save it as per the previous section.