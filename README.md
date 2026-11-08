# Cafe au Lait

<p align="center"><img src="branding/icon.png" alt="Cafe au Lait" width="128"></p>

Cafe au Lait is a Wii U homebrew app and a Windows importer that bring **your own** console system and account files into [CemuX](https://github.com/GamesExObscura/CemuX), so CemuX can run its native Wii U Menu, HOME, manuals and online features with your own data.

It is built on [Dumpling](https://github.com/dumpling-app/dumpling)'s dump layout. Thank you to the Dumpling, libmocha and WUT authors.

## How it works

1. Run the Cafe au Lait app on your own Wii U. It needs an existing homebrew environment (Aroma/Tiramisu with Mocha services).
2. In CemuX, choose **File > Import Wii U System (Cafe au Lait)...**, enter the Wii U's private IPv4 address and approve the transfer. The console shows a pairing code that you compare and approve on the console.
3. The app copies files from the console to your PC over your local network. The PC verifies every file against a manifest before importing, then sets up a **new** CemuX profile and restarts into it.

Your existing CemuX settings, saves, accounts and game files are never merged over or replaced.

## Safety

- Console file access is **read-only**. All files are opened in read mode, and the app links no file-write, format, install or raw-storage functions.
- It reads the internal MLC, and your OTP/SEEPROM and a few native libraries needed for online use. It does not include USB or disc volumes.
- The transfer is **not encrypted**. Use it only on a trusted home network and never expose it to the Internet. Internet addresses and host names are rejected.
- The mount used for one of the system partitions is a normal filesystem mount, not a hardware read-only sandbox. No tool can guarantee zero risk to a console, so use it at your own risk.
- No Nintendo system files, keys, fonts or account data are included in this repository. Each user must dump their own.

See [SAFETY.txt](SAFETY.txt) for the full scope.

## Download

The Wii U app is in [Releases](../../releases). Unzip it to the root of your SD card so it ends up at `SD:/wiiu/apps/cafe-au-lait/`. The Windows side ships inside CemuX (`cafe-au-lait` folder beside `CemuX.exe`).

## Status

- Version 0.2.2. A full transfer and import worked on the author's console and reached the Wii U Menu in CemuX. Other consoles, firmware setups and Pretendo accounts have not been tested.
- The PC side is written for CemuX and is not a general-purpose tool.

## Source

- `console/` is the Wii U app source (C++, devkitPPC and WUT, with libmocha).
- `pc/` is the Windows importer (C# launcher and PowerShell modules).
- `SD-card/` is the built Wii U app (`.rpx` and `.wuhb`). `branding/` is the artwork.
- A build script for the console app is not included yet. You need devkitPPC, WUT and libmocha, and the compile and link steps are straightforward but undocumented.

## License

GPL-3.0, see [LICENSE](LICENSE). Third-party components keep their own licenses (Dumpling MIT, libmocha LGPL-3.0, WUT zlib); see [THIRD-PARTY.txt](THIRD-PARTY.txt).
