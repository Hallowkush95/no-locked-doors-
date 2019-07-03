There is a lot of different factors that can prevent you from downloading miner files.<br>
The most common are:
1. Anti-Virus removing files
2. Unable to access miner download link

### Anti-Virus removing downloaded miner files

To fix this issue, you have to add an exception in your AV. It is best to add the whole NHM folder. <br>
If you don't have AV you must add exception to Windows Defender inside Virus & threat protection.

If this doesn't work try to fix the issue with the following methods.

### Unable to access miner download link

This is possible due different reasons (link is broken, internet provider blocked miner site IP address, etc.).
To fix this issue replace the `miner_mins_urls.json` file with the following:
* https://github.com/nicehash/MinerDownloads/releases/download/v1.0/miner_bins_urls.7z
* https://github.com/nicehash/MinerDownloads/releases/download/v1.0/miner_bins_urls.zip

First try to download with 7z file and if that doesn't work use zip file.

If none of this works try to download miner file manually.

After these steps you should have miner file downloaded and ready to mine.
