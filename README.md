# Taira Releases

## Windows 下載

[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本：`1.2.12`  
支援：Windows 11 x64

標準 Windows Installer (MSI)，不再使用自解壓 EXE。

Public Windows distribution for Taira.

The only update artifact is:

- `TairaSetup.msi`

Taira downloads the MSI directly from this repository, reads its Windows Installer version metadata, and upgrades through `msiexec`.

No update manifest, payload ZIP, private key, or internal configuration is published here.
