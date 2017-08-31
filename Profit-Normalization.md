# Profit Normalization

As of NHML 1.8.1.2, Profit Normalization is available to mitigate unnecessary switching after quick spikes in any algorithm's paying rate. Buyers may post small orders on NiceHash to draw away miners for short periods of time, but it can lead to miners switching too frequently and losing some profit (e.g. issue [#225](https://github.com/nicehash/NiceHashMinerLegacy/issues/225)).

The normalization feature attempts to detect unlikely short spikes in paying rates, and normalize them down to practical levels. If the paying rate stays high for some time, it will be reported as normal.

## Customizing Normalization

NHML uses a simple statistic method of determining outlying paying rates. If the paying rate received by NHML is higher than the third quartile (3Q) by a certain number of inter-quartile ranges (IQRs), it is normalized downward. There are three variables that can be customized by editing `\configs\General.json`:

* `IQROverFactor`: This is the number of IQRs the new profit has to be above the 3Q in order to be flagged as deviant. The lower this value, the more resistant NHML will be to upward profit spikes. The default is 3.0.

* `NormalizedProfitHistory`: The number of past profits to use for getting trends. The higher this value, the more resistant NHML will be to upward profit spikes. The default is 15. Normalization will not happen until this many profit values have been received.

* `IQRNormalizeFactor`: The number of IQRs above 3Q a deviant rate is normalized to. The lower the value, the more resistant NHML will be to upward profit spikes. The default is 2.0. It would not make sense to set this higher than `IQROverFactor`.

When adjusting these values, you may find it useful to watch the log after each incoming paying rate. If an algorithm is deviant, you will see lines such as 

## Example

If using the default values, after 15 profits have been received by NHML, rates will be scrutinized for spikes. Say X11Gost has been paying 0.020 +/- 0.005 for the 15 past values, and on the next rate notification it has jumped to 0.18. The IQR for the past values may be around 0.005, and so this rate is far above the 3 IQRs (0.015) above the 3Q (0.0225). Therefore the rate will be normalized to 2 IQRs above the 3Q (0.01 + 0.0225 = 0.0235). 

As more values come in, the last 15 rates will become significantly more varied if the paying rate stays around 0.18, and so the normalization will quickly become less strong until dropping off completely. If, after that, X11Gost were to drop back down to 0.020, there will be no normalization (the normalization is only for upward spikes). 