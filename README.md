# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.70
支援: Windows 11 x64

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.70
支援: macOS 12+ / Apple Silicon

## 本次更新（1.2.70）

- 修復 iPad mini、iPadOS Retina 裝置連線時，Mac 桌面被錯誤縮在中央並出現過大黑邊的問題。
- 改為依 iPad 實際 CSS 視窗寬度等比例適配，保留 Mac 桌面比例；不再用遠端像素除以 iPad DPR 限制畫面寬高。
- 直向／橫向轉換及 iPad 可視範圍變化時重新計算縮放與移動邊界，保留既有觸控、編碼與安全功能。
- 213 項 Node 測試通過（包含 iPad 顯示回歸測試）；client build 89、cache taira-v105。
- Windows／macOS 正式更新套件簽章已驗證；更新 Host 後請重新整理 iPad 上的 Taira PWA，並檢查直向、橫向與觸控座標。

## 前版更新（1.2.69）

- 盤點並校正編碼設定，保留自動／画質／速度／遊戲四種偏好，不新增文字清晰模式。
- 畫質優先以 1080p30 的 12 Mbps 為基準，依來源像素及 FPS 調整、最多 25 Mbps；720p30 約 5.33 Mbps，避免低於同尺寸的自動／速度預算。
- 速度優先 1080p30 名義碼率從 9 降至 4.5 Mbps；720p30 約 3.75 Mbps，來源較小時降低預算。這是設定目標，不保證實際流量固定比例下降。
- 編碼偏好選自動時可自訂解析度／FPS；明確圖片格式關閉無作用的影音覆寫。
- Windows JPEG 擷取最多 30 FPS，公開檔位與瀏覽器選項對齊能力，避免啟動無法使用的 H.264 TCP／WebRTC 通道。
- 原生尺寸、FPS、格式與碼率先正規化再比較，避免被限制的重複設定反覆重建 encoder。
- 低延遲模式若不支援可選速度／品質提示會記錄原因；仍保留低延遲、硬體編碼與影格不重排。
- 保留來源像素上限、1.2.68 影格／緩衝修正、P0 弱網降載、安全重連與 H.265 優先及 H.264 回退。

221 項本地測試通過。Client build 88 / cache taira-v104。
MSI 與 Sparkle 更新簽章、Mac packaged Bun Host、唯讀 DMG 掛載及 codesign deep strict 驗證通過。

更新後重新整理遠端頁面。實際畫質、流量與長時間弱網表現仍需遠端連線量測。
