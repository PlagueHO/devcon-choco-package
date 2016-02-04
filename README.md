# devcon-choco-package
Chocolatey package definition for installing DevCon (Microsoft Device Console)

## Project Details
This project contains several files:
1. AppVeyor.yml - the AppVeyor.YML CI definition that will automatically build the DevCon.exe and package it into a Nuget package for submission to Chocolatey.
2. Devcon.Portable.Nuspec - the Chocolatey package definition.

When changes to the repo are committed, an AppVeyor CI build will be triggered which will:
1. Clone the [Windows Driver Samples ](https://github.com/Microsoft/Windows-driver-samples) repository.
2. Build the DevCon.exe application from the \Setup\DevCon folder of the repository.
3. Copy the DevCon.exe to the devcon.portable folder.
4. Set the version number of the Chocolatey package definition (devcon.portable.nuspec) to match the AppVeyor build version.
5. Use the Chocolatey cpack command to build the Chocolatey package.
6. Upload the new package as an artifact (e.g. devcon.portable.10.0.10586.9.nupkg)
