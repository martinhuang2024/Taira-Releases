# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.75
支援: Windows 11 x64

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.75
支援: macOS 12+ / Apple Silicon

## 本次更新（1.2.75）

- iPhone 12 mini／其他手機新增「畫面顯示」選擇：完整畫面保留桌面全部內容；填滿螢幕等比例放大、減少長寬比造成的黑邊，但會裁切邊緣，可透過三指手勢移動查看。
- 依遠端畫面比例與手機視窗動態計算滿版縮放，轉向、畫面更新時維持合適比例；不拉伸變形，也保留既有點擊座標與雙指縮放。
- 預設完整畫面，避免手機直向時大量裁掉桌面；右上角設定可切換「填滿螢幕」並記住選項。
- 包含前版的錯誤動態碼自動清除與 iOS 安全區修正。225 項 Node、10 項 Windows MSI 測試通過。Client build 94、PWA cache taira-v110；Mac/Windows 簽章版同步更新。
- 更新 Host 後重新開啟手機 Taira PWA，在右上角設定切換填滿螢幕，實測黑邊與觸控位置。

## 前版更新（1.2.74）

- 驗證器六位動態碼輸入錯誤或已使用時，收到 `invalid_otp` 後立即清空輸入欄，顯示錯誤訊息並回到輸入欄，方便重新輸入；不影響已驗證裝置與其他連線錯誤處理。
- iPhone 12 mini 主畫面 PWA 可使用狀態列後方的頂部安全區域；保留瀏海、系統限制與完整遠端畫面等比例顯示，不強制裁切桌面。使用 Safari 網址列時仍由 iOS 管理瀏覽器區域。
- 已通過 223 項 Node 回歸測試及 10 項 Windows MSI 測試。Client build 93、app.js?v=107、PWA cache `taira-v109`。兩平台正式安裝檔沿用既有 Ed25519/Sparkle 更新簽章。
- 更新被控端到 1.2.74，重新開啟 iPhone 主畫面 Taira；請實機確認頂部顯示空間與錯誤動態碼重新輸入。

## 前版更新（1.2.73）

- 修復一般／自動模式仍把 WebRTC 接收端影格等待時間錯當作網路壅塞的問題，避免快速移動畫面時即使沒有丟包，碼率仍連續降至 15% 下限。
- 同步修復碼率恢復條件：畫面緩衝偏高，但實際網路健康時允許逐步恢復；保留真實丟包、RTT 異常、網路 jitter、佇列壅塞與解碼掉幀的保護。
- 加入 iPad「複製瀏覽器診斷」的輸入確認往返、Host 處理時間與控制 RTT，和畫面緩衝等待分開記錄，協助區分點擊指令延遲、視覺回饋延遲。
- 使用 1.2.72 現場 Log 當作回歸測試案例，原先會失敗，修正後通過；221 項 Node 及 10 項 Windows MSI 測試通過。
- 前端 build 92、PWA cache taira-v108；Windows MSI 與 macOS DMG / appcast 均使用既有更新金鑰簽章及驗證。
- 更新 Host 後重新開啟 iPad PWA，測試快速拖曳、點擊回饋及畫面延遲。平均 WebRTC buffer 不等同於精確的端到端點擊耗時，仍需實機測量。

## 前版更新（1.2.72）

- 修正快速變動畫面時，WebRTC 接收端的影格等待時間被誤認為網路抖動，造成遊戲模式持續降碼率、畫面卡頓的問題。
- 只有出現真實丟包、封包 jitter、RTT 持續暴增、送出佇列壓力等訊號時，才依原本保護機制調降碼率；仍保留接收端持續凍結時的 60→30 FPS 回退。
- 增強 iPad PWA 複製瀏覽器診斷：解碼 FPS、掉幀、freeze、真正網路 jitter、影格等待時間、RTT 與接收碼率可分開觀察。
- 以實際異常數據先重現失敗再修正，218 項 Node 測試及 10 項 Windows MSI 測試通過。Client build 91、PWA cache taira-v107。
- Windows MSI 使用既有 Ed25519 金鑰簽章；macOS DMG / appcast 使用既有 Sparkle 金鑰簽章，版本、封裝與簽章皆通過驗證。
- 更新 Host 後請重新開啟 iPad PWA 測試快速滑動、視窗移動、遊戲模式及 1.2.71 的無上限縮放。

## 前版更新（1.2.71）

- 雙指放大解除 4 倍上限，也不再受遠端桌面原生像素或 iPad Retina DPR 限制，放大僅作用在本機畫面呈現，不提升串流編碼解析度。
- 縮小最低回到螢幕適配的 1 倍，不會繼續縮成小框；縮回 1 倍時重設偏移。
- 保留雙指縮放中心點、三指移動畫面、滑動捲動、輸入座標及視窗旋轉／大小調整；新增非有限縮放數值保護。
- 215 項 Node 與 10 項 Windows MSI 測試通過。Client build 90／PWA cache taira-v106。
- macOS DMG 已以既有 Sparkle 金鑰簽章並通過唯讀掛載及程式碼簽章檢查；Windows MSI 已以既有 Ed25519 更新金鑰簽章並通過版本及內容驗證。
- 更新 Host 後重新整理 iPad 的 Taira PWA，再測試直向、橫向與縮放／觸控座標。

## 前版更新（1.2.70）

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
