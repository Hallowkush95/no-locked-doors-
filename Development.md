To get started on development you will need Visual Studio 2017. The main project currently targets Windows 8.1 SDK and .NET Framework 4.5 so make sure to install those, as well as .NET desktop development.

Once VS is setup, open `NiceHashMinerLegacy.sln` in VS. You will see multiple projects, with the main one being `NiceHashMinerLegacy`. From there you can build and debug the program.

The misc. projects target VC++ 2013, which is currently unopenable in the newest VS. For the moment you can just copy their .dll and .exe files from the main release since they are not updated often.

Pull requests are welcome, but if you make an update that modifies the miner files you will have to coordinate with me since they are downloaded separately and the sources need to be verified. There is no set formatting used, but please try to not have VS automatically format existing code. This clutters your PR with format changes ('{' moving down a line etc) and can make it hard to see what you are actually changing.