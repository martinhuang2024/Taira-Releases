# Taira Releases

## Windows

[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.60
支援: Windows 11 x64

Windows 1.2.60 同步串流擁塞控制、Capture 復原、WebSocket 心跳及診斷改進。透過 OrbStack Docker + WiX 相容 MSI 建置流程完成；已驗證 23 個檔案 SHA-256、MSI 升級碼、更新通道、既有程序關閉與重新啟動動作、以及 Ed25519 更新簽章。Windows 實機安裝與從舊版升級仍待驗證。

## macOS

[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.60
支援: macOS 12+ / Apple Silicon

macOS 1.2.60 改善 WebRTC 動態碼率震盪、Capture 無影格自動恢復、WebSocket 心跳與診斷紀錄；已通過 JS／Rust 測試、packaged Bun Host smoke、DMG 掛載與 codesign 驗證。
