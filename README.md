# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.63
支援: Windows 11 x64

修正畫質優先降解析度後未回升：JPEG/HEIC 改依相對連線基準的 ACK 延遲，持續穩定 30 秒後逐級試升；小影格不再被誤判為頻寬不足。WebRTC 保留冷卻期內的回升請求，quality 模式在壅塞 hold 結束後加快碼率恢復。固定解析度與 speed 720 上限保留。182 項本地測試通過，更新包沿用正式 Ed25519 簽章。

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.63
支援: macOS 12+ / Apple Silicon

相同修正原始碼打包；通過 packaged Bun Host 健康檢查、唯讀 DMG 掛載、App codesign deep strict 及 Sparkle 更新簽章驗證。

回升已以可重現的降級／穩定恢復測試驗證，實際網路效果仍需使用中觀察。
