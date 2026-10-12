# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.64
支援: Windows 11 x64

修正卡住後顯示舊影格的恢復缺口：JPEG/HEIC 限制解碼時間、只保留最新待解碼影格；WebCodecs 丟棄逾時與倒序輸出。相對兩端經過時間偵測延遲 TCP history，不要求時鐘同步。MSE 排隊逾時切回 JPEG，不任意刪除 H.264 參考影格；RTP send 停滯後停止續送舊 frame 並要求 keyframe。已交給網路的封包無法撤回。

190 項本地測試通過，包含 8 個 late decode／倒序／MSE backlog／RTP pause 故障模擬。沿用正式 Ed25519 更新簽章與既有 MSI 修正。Client build 83 / cache taira-v99。

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.64
支援: macOS 12+ / Apple Silicon

相同修正原始碼打包；發布前驗證 packaged Bun Host、唯讀 DMG 掛載、App codesign deep strict 與 Sparkle 更新簽章。

尚未將使用者的實際卡住事件唯一歸因到某個 transport；實际網路效果仍需使用觀察。
