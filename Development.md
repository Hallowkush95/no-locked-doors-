To get started on development you will need Visual Studio. The main project currently targets Windows 8.1 SDK and .NET Framework 2.0 (soon to be upgraded to 4.5) so make sure those, as well as .NET desktop development.

The misc. projects target VC++ 2013, which is currently unopenable in the newest VS. For the moment you can just copy their .dll and .exe files from the main release since they are not updated often, but soon they will be upgraded to support VS2017.

Once you have the project open make sure the NuGet packages are downloaded (currently only necessary for the `develop` branch).

I welcome pull requests, but if you make an update that modifies the miner files you will have to coordinate with me since they are downloaded separately.