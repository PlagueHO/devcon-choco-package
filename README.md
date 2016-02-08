# devcon-choco-package
Chocolatey package definition for installing DevCon (Microsoft Device Console)

## Project Details
This project contains several files:
 1. AppVeyor.yml - the AppVeyor.YML CI definition that will automatically build the DevCon.exe and package it into a Nuget package for submission to Chocolatey.
 2. Devcon.Portable.Nuspec - the Chocolatey package definition.
 3. Devcon32.exe - the 32-bit Devcon.exe found in the Windows Driver Kit (WDK) for Windows 10. MD5: b14f9ffbeaaab08167e6223cac933b22
 4. Devcon64.exe - the 64-bit Devcon.exe found in the Windows Driver Kit (WDK) for Windows 10. MD5: 79c8395d54fa2e32425a56807240523b

## Current Project Process
 1. Set the version number of the Chocolatey package definition (devcon.portable.nuspec) to match the AppVeyor build version.
 2. Use the Chocolatey cpack command to build the Chocolatey package.
 3. Upload the new package as an artifact (e.g. devcon.portable.10.0.10586.9.nupkg)

## Deprecated Project Process
The original intent of this project was to build the DevCon.exe files directly from the MSFT published source code, but this produces application files that are unverifiable.
So this project has been updated to use the Devcon.exe application files that are installed with the WDK.
This allows MD5 hashes of the Microsoft published Devcon application files to be verified.

The deprecated process documentation is as follows:

When changes to the repo are committed, an AppVeyor CI build will be triggered which will:
 1. Clone the [Windows Driver Samples ](https://github.com/Microsoft/Windows-driver-samples) repository.
 2. Build the DevCon.exe application from the \Setup\DevCon folder of the repository.
 3. Copy the DevCon.exe to the devcon.portable folder.
 4. Set the version number of the Chocolatey package definition (devcon.portable.nuspec) to match the AppVeyor build version.
 5. Use the Chocolatey cpack command to build the Chocolatey package.
 6. Upload the new package as an artifact (e.g. devcon.portable.10.0.10586.9.nupkg)
