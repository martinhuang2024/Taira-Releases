# Taira Releases

## Windows
[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.81
支援: Windows 11 x64

## macOS
[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.81
支援: macOS 14+ / Apple Silicon

## 本次更新（1.2.81）

- macOS 選單列與 Windows 系統匣將原本獨立的「建立 Passkey QR」入口合併進「重設安全設定」子選單。裡面有「建立 Passkey QR…」及「重設全部驗證設定…」兩項，後者仍必須確認才會清除設定。
- 將「已驗證裝置」改名為「撤銷已驗證裝置」，保留各裝置資訊、個別撤銷確認和連線終止功能。
- 不修改現有 Passkey、Bitwarden、動態碼或已儲存的工作階段。只更新原生 Host 選單及版本，瀏覽器 PWA 不需額外清快取。
- 251 項 JavaScript、28 項 Rust、10 項 MSI Python 測試通過；Mac Capture 建置、Bun Host 啟動、macOS 14 App 簽章與 Sparkle 更新簽章驗證成功。Windows Rust Host／MSI 建置及正式 Ed25519 更新簽章通過。
- macOS／Windows 的原生選單外觀仍需在實際設備上確認。

## 前版更新（1.2.80）

- 首次設定可由 Host「安全設定 · 首次建立 Passkey QR…」產生 QR：Mac 選單列或 Windows 系統匣點選，限 2 分鐘、只能完成一次註冊。手機掃描後開啟 Host 的 Tailscale HTTPS 專屬設定頁，使用 Bitwarden 或系統提供的 Passkey 完成 WebAuthn 註冊。**掃描本身不會取得遠端控制權**。
- 第一次設定可直接選 Passkey，不必先信任裝置或建立六位數 TOTP。原本使用 TOTP 的裝置仍可繼續使用；登入方式保持 Passkey 與 TOTP 二選一。
- macOS 原生 QR 介面開始移至 **Swift + SwiftUI**：首次 Passkey QR 視窗及 TOTP/Passkey QR 產生改由 `native/TairaSecurityViews.swift` 負責。Objective-C 暫保留影像擷取及選單列橋接，後續將逐模組遷移，不會假裝全部已改為 Swift。
- 不再為舊版 macOS 額外維護介面兼容：**最低 macOS 14.0**。Mac App Bundle 和 Sparkle appcast 都明確標示 14.0。
- Windows 使用 Rust Host 原有 QR 視窗展示一次性 Passkey 設定連結。新頁面有清楚的新增 Passkey 按鈕，QR 失效或驗證失敗時會拒絕註冊。
- 249 項 JavaScript、28 項 Rust、10 項 MSI Python 測試通過。Mac Capture + SwiftUI 編譯、Bun Host 啟動、DMG 掛載與簽章均通過；Windows Rust Host 已跨平台建置，MSI 使用正式 Ed25519 金鑰簽章。
- 版本 `1.2.80`、client build `100`、app.js?v=114、passkey.js?v=2、PWA cache taira-v116。Bitwarden 選擇視窗、手機掃碼註冊及 Windows 實機安裝仍需在實際設備驗證。

## 前版更新（1.2.79）

- 重整 PWA 時，先從 Host 確認前端版本再開啟登入畫面，解決登入畫面短暫閃現、舊前端在輸入動態碼後才跳出更新、更新後需要再輸入一次的流程問題。新版會對每個 Host build 自動嘗試一次前端快取清理；檢查失敗則顯示重新檢查按鈕，不先消耗動態碼。
- 登入方式改為「六位數動態碼」或「Passkey」**二選一**。新電腦不必先執行「信任此裝置」。支援標準 WebAuthn 的 Bitwarden、其他密碼管理器及系統 Passkey；跨裝置手機掃 QR 由瀏覽器提供，是否顯示 QR 視瀏覽器及裝置支援而定。登入後可直接按「新增 Passkey」註冊。
- 控制端移除整個「裝置安全／信任此裝置」區塊，以及重複的「畫面顯示」完整／填滿切換；自適應畫面、縮放與手勢保留。過去裝置金鑰不能再單獨換取登入工作階段。
- Mac Host 選單與 Windows Host 系統匣新增「已驗證裝置」清單，顯示可辨識的裝置類型、驗證方式和連線狀態。可選擇單台裝置撤銷工作階段並中斷連線；用戶仍可以再次使用有效的動態碼或 Passkey 登入。此功能不會刪除 Bitwarden／系統儲存的 Passkey。
- 將 `dist/app.js` 的 Passkey 與 Session 拆成 `dist/passkey.js`、`dist/auth-client.js`；Host 的裝置管理拆成 `host/device-management.mjs`，降低登入功能與畫面串流耦合。
- 247/247 JavaScript、28/28 Rust、10/10 MSI Python 測試通過。macOS 簽章 DMG 已驗證、封裝 Bun Host 啟動正常；Windows MSI 已使用正式 Ed25519 更新金鑰簽章並核對內容與升級設定。
- 版本 1.2.79、client build 99、app.js?v=113、styles.css?v=87、PWA cache taira-v115。更新 Host 後請重新開啟 PWA；真實 Bitwarden 選擇視窗、手機跨裝置 QR 及 Windows 實機安裝仍需在設備上確認。

## 前版更新（1.2.78）

- 修正手機及窄視窗中「裝置安全」區塊的按鈕排版：將「1. 信任此裝置」與「2. 啟用 Passkey」改成一致寬度、上下排列、容易點選的按鈕，避免原本 Passkey 長文字換成多行。
- 精簡 Bitwarden／Passkey 說明，改用中性說明樣式，不再整段顯示紅色警告背景；狀態列或裝置清單沒內容時不顯示空白框。
- 不更動原本 TOTP、裝置金鑰及 WebAuthn/Bitwarden 登入流程。新增三項 CSS 與 PWA 回歸測試，總計 243 項 JavaScript、28 項 Rust、10 項 MSI Python 測試通過。
- Windows MSI 與 macOS DMG 均使用既有正式更新金鑰簽章並驗證。Client build 97、app.js?v=111、styles.css?v=86、PWA cache taira-v113。
- 將 Host 更新至 1.2.78 後，重新開啟手機 PWA 並檢查設定面板按鈕。此版尚未完成真實手機畫面驗證。

## 前版更新（1.2.77）

- 新增真正的標準 WebAuthn Passkey，供 Bitwarden、1Password、系統鑰匙圈或 Windows Hello 等符合標準的提供者使用；在瀏覽器按「啟用 Passkey」，由瀏覽器／密碼管理器決定保存位置。這不是專屬 Bitwarden API，不要求安裝特定 App。
- 首次仍要輸入原本六位數動態碼並「信任此裝置」。之後使用這台瀏覽器獨立裝置金鑰加上 Passkey 驗證登入；同步到密碼管理器的 Passkey 可以讓**其他已信任的瀏覽器**共用，不能跳過新瀏覽器的裝置授權。
- 相容沒有指紋或臉部辨識硬體的電腦：WebAuthn 要求使用者在密碼管理器／裝置上確認，驗證層級為 `userVerification: preferred`，**不保證每次都觸發生物辨識或 PIN**；既有 TOTP 留作復原用途。
- 可以在設定新增多把 Passkey 或手動移除本台 Host 上的所有 Passkey；撤銷單台裝置金鑰不會誤刪共用的密碼管理器 Passkey。驗證僅允許 Host 原始 Tailscale HTTPS 網域，挑戰一次有效、90 秒失效。
- 240 項 JS、28 項 Rust、10 項 MSI Python 測試通過，包含真實 WebAuthn 加密簽章與跨裝置測試。macOS 封裝 Bun Host 啟動測試、程式碼簽章、DMG 掛載與 Sparkle 簽章均驗證通過；Windows MSI 正式 Ed25519 簽章、升級設定與內容已驗證。
- Client build 96、app.js?v=110、PWA cache taira-v112。更新兩平台 Host 後，請在真實電腦的 Bitwarden 擴充功能／手機 PWA 測試建立與使用 Passkey。尚未實機驗證所有密碼管理器與跨裝置平台組合。

## 前版更新（1.2.76）

- 新增「信任此裝置（免動態碼）」：使用 P-256 不可匯出裝置私鑰（WebCrypto / IndexedDB）替已登入的瀏覽器綁定獨立身分，之後可驗證裝置金鑰後建立控制端 Session。
- 設定頁可查看已授權裝置、單獨撤銷，撤銷時清除該瀏覽器現有 Session 並中斷控制連線；驗證挑戰 90 秒過期且只能使用一次。
- 保留現有 TOTP 六位數登入與復原方式，不自動強制切換。這是第一階段的裝置金鑰功能，**尚非 WebAuthn Passkey／Face ID／Touch ID，也不是每台裝置掃 QR 後由 Host 逐台核准**。
- 已通過 233 項 JavaScript、28 項 Rust 和 10 項 Windows MSI Python 測試；Windows MSI 使用既有 Ed25519 正式金鑰簽章，macOS DMG／Sparkle 使用既有正式金鑰簽章並完成掛載、程式碼簽章及封裝 Bun Host 啟動測試。
- Client build 95、app.js?v=109、PWA cache taira-v111。更新 Host 後請重新開啟 iPhone／iPad PWA，再手動選擇是否信任目前裝置；首次設定及裝置撤銷仍建議實機驗證。

## 前版更新（1.2.75）

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
