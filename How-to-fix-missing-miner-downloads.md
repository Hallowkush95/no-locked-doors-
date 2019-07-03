There is a lot of different factors that can prevent you from downloading miner files.<br>
The most common are:
1. Anti-Virus removing files
2. Failed autodownload

### Anti-Virus removing downloaded miner files

To fix this issue, you have to add NHM folder as an exception in your AV.<br>
For example if you have Windows Defender, add exception inside Virus & threat protection settings.

If this doesn't work, try to fix the issue with the following method.

### Failed autodownload
If autodownload fails, download the miner bins manually and unzip them to the miner plugin `bins` path.
If you wish to upgrade to a newer miner binary set **use_file_settings** to **true** (`"use_file_settings": true`) and replace URL for your target miner in `miner_bins_urls.json` file.



After these steps you should have miner file downloaded and ready to mine.
