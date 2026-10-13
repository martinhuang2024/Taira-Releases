# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.68
支援: Windows 11 x64

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.68
支援: macOS 12+ / Apple Silicon

## 本次更新

- 修正品質參數比對不一致造成的編碼器反覆重建；單純碼率調整沿用既有編碼器，避免重複關鍵影格突發。
- 畫質優先不再只因接收端緩衝偏高而持續降碼率；仍依丟包、網路抖動、RTT 突升與傳送壅塞降載，網路穩定後逐步恢復。
- 畫質優先以 1080p30 的 8 Mbps 為基準，依實際像素與 FPS 調整，最高 25 Mbps。這是編碼目標，實際流量依內容與連線狀況而定。
- 提高畫質優先圖片備援品質；保留被控螢幕原生像素上限與四種既有偏好，無新增文字清晰模式。
- 保留 P0 弱網降載、同一控制端重連的安全碼率、TCP 備援、前景三秒停格恢復及 H.265 優先與 H.264 回退。
- Windows 本機擷取仍為 JPEG。

215 項本地測試通過，含原生品質／碼率更新回歸測試。Client build 87 / cache taira-v103。
MSI 與 Sparkle 更新簽章、Mac packaged Bun Host 與 codesign deep strict 驗證通過。

更新後重新整理遠端頁面。實際清晰度與流暢度需於遠端連線確認。
