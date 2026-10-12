# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.67
支援: Windows 11 x64

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.67
支援: macOS 12+ / Apple Silicon

## 本次更新

- 移除獨立「文字清晰」選項，改善整合進原有「畫質優先」。保留自動／畫質／速度／遊戲四種編碼偏好。
- 畫質優先保留被控螢幕原生像素（最長邊最多 8192），以 30 fps、最多 6 Mbps 目標碼率起步；壅塞時降低至 20／12 fps 並調整碼率。
- 已儲存的舊文字清晰設定自動轉換成畫質優先。
- 保留 P0 弱網降載、同一控制端重連的安全碼率與檔位、TCP 備援降載與前景三秒停格恢復。
- 擷取、瀏覽器顯示與觸控放大不超過被控螢幕實際像素，保留寬高比與像素密度處理。
- 保留自動 H.265 優先與 H.264 相容回退；Windows 本機擷取仍為 JPEG。

212 項本地測試通過。Client build 86 / cache taira-v102。
MSI 與 Sparkle 更新簽章、Mac packaged Bun Host、唯讀 DMG 掛載及 codesign deep strict 驗證通過。

更新後重新整理遠端頁面。文字清晰度改善已整合至畫質優先，無需選擇新增模式。實際清晰度與流暢度仍取決於瀏覽器和連線環境。
