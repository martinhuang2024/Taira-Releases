# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.65
支援: Windows 11 x64

自動模式及 TCP 背景恢復優先協商 H.265/HEVC，瀏覽器需提供支援。HEVC 失敗時約 1 秒後改試 H.264，並暫緩 HEVC 重試 5 分鐘；明確 H.264／不支援 HEVC 時維持 AVC。背景協商保留 TCP 解碼器，已正常播放的 RTC 不強制重建。Windows 本機擷取仍為 JPEG；HEVC 策略適用相容 Mac RTC Host。

194 項本地測試通過。Client build 84 / cache taira-v100，保留畫質回升與過期影格修正，沿用正式 Ed25519 更新簽章。

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.65
支援: macOS 12+ / Apple Silicon

相同原始碼打包；已通過 packaged Bun Host、唯讀 DMG 掛載、codesign deep strict 與 Sparkle 更新簽章驗證。

編碼策略與回退以模擬測試驗證；流暢度仍取決於實際瀏覽器與連線。更新後請重新整理遠端頁面。

本地版本驗證：Mac 與 Windows 均已更新至 1.2.65；Windows MSI 回傳碼 0，兩端 Host 與擷取程序正常。網頁版本 build 84 / cache taira-v100，Mac 提供的 app.js 與發布原始碼一致。
