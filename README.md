# Taira Releases

## Windows

[下載 TairaSetup.msi](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/TairaSetup.msi)

目前版本: 1.2.62
支援: Windows 11 x64

補上閒置畫面恢復：前景影像解碼超過 5 秒或畫面通道 15 秒未收到訊息時自動重連；分別檢查畫面與操作通道心跳，丟棄舊串流延遲完成的影格。176 項本地測試通過，沿用正式 Ed25519 更新簽章與已修復的 MSI 打包流程。長時間實機閒置仍需觀察。

## macOS

[下載 Taira.dmg](https://raw.githubusercontent.com/martinhuang2024/Taira-Releases/main/Taira.dmg)

目前版本: 1.2.62
支援: macOS 12+ / Apple Silicon

已從相同原始碼重建，通過 packaged Bun Host 健康檢查、DMG 掛載、App codesign 驗證及 Sparkle 更新簽章驗證。

Windows 實機驗證：從 1.2.61 升級，MSI 回傳碼 0；安裝尾段第一次啟動遇到 EBUSY 檔案鎖，安裝結束後重新啟動成功。Host 回報 1.2.62 / client build 82，Host 與擷取程序正常，登入與驗證器設定檔雜湊未變更。
