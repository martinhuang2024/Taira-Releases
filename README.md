# Taira Releases

## Windows

[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.61
支援: Windows 11 x64

修正 MSI 升級後啟動失敗（2753）：補齊 EXE 版本與語言資訊、修正 MSI 字串表計數，並支援同版本重裝。已完成 Mac 交叉編譯、168 項本地測試及正式 Ed25519 更新簽章；安裝流程已在 Windows 驗證，全新發布包的實機升级驗證進行中。

## macOS

[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.61
支援: macOS 12+ / Apple Silicon

已從相同原始碼重建，通過 packaged Bun Host 健康檢查、DMG 掛載、App codesign 驗證及 Sparkle 更新簽章驗證。
