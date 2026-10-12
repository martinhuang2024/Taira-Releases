# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.66
支援: Windows 11 x64

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.66
支援: macOS 12+ / Apple Silicon

## 本次更新

- 弱網嚴重壅塞時更快降低碼率與自動檔位；自動 FPS 可降至 20／12。手動固定解析度／FPS 與遊戲策略仍保留。
- 同一控制端重連保留最近安全碼率與檔位；TCP 備援接續降載，RTC 重試保留 TCP 的後續降載結果，穩定後逐步恢復。
- 回前景要求新影格；約三秒沒有恢復畫面就切換備援。
- 新增「文字清晰（原生解析度，12–30 fps）」編碼偏好：保留被控螢幕原生像素（最長邊最多 8192），初始目標最多 6 Mbps，壅塞時優先降低更新率與碼率。
- 擷取、瀏覽器顯示及觸控放大不超過被控螢幕實際像素，保留寬高比，支援直向螢幕與瀏覽器像素密度。
- 保留自動 H.265 優先與 H.264 相容回退；Windows 本機擷取仍為 JPEG。

211 項本地測試通過。Client build 85 / cache taira-v101 / styles v84。
MSI 更新簽章、Sparkle 更新簽章、Mac packaged Bun Host、唯讀 DMG 掛載及 codesign deep strict 驗證通過。

更新後重新整理遠端頁面。看文件時可在設定啟用編碼偏好，選擇「文字清晰」；串流目標碼率與實際傳輸量不同，實際清晰度與流暢度仍需在使用環境驗證。

本地安裝驗證：Mac 與 Windows 均已更新至 1.2.66 / client build 85。Windows MSI 回傳碼 0；兩端 Host、輸入與擷取程序正常。Mac HTTPS 網頁已確認可載入新解析度模組與「文字清晰」選項。
