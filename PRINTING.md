# 多裝置列印

GitHub 網頁的「列印設定」集中管理連接方式。工作台的自動列印文字為「訂單(結帳)自動列印」。

| 方式 | 條件 | 自動列印 |
| --- | --- | --- |
| Windows 驅動 USB | 啟動本機 Windows 列印程式並配對 | 可啟用 |
| Android USB | 裝置支援 OTG、Chrome 提供 WebUSB、印表機有可用 Bulk OUT 介面 | 連接成功後可啟用 |
| 藍牙 SPP | 印表機支援 ESC/POS 與標準 SPP，先在系統藍牙配對，瀏覽器提供 Web Serial | 連接成功後可啟用 |
| 藍牙 BLE | 瀏覽器提供 Web Bluetooth，印表機支援 ESC/POS，需廠商的 Service／可寫入 Characteristic UUID | 連接成功後可啟用 |
| 系統列印／AirPrint | 作業系統有可用印表機；iPhone／iPad 需 AirPrint 相容印表機與相同網路 | 需手動確認 |

不支援的連接方式依瀏覽器能力停用。舊 Android／Chrome 不一定提供 SPP；Android WebView 與獨立 Chrome 的能力也不同。本次為 GitHub 網頁更新，不是 Android APK 更新。

紙寬、切紙設定用於 USB／藍牙 ESC/POS 出單；系統列印的紙張與切紙由系統驅動設定。

藍牙需印表機硬體本身支援。SPP 與 BLE 不可互換，BLE UUID 不可任意猜測。確認廠商規格後，先測試中文出紙，再開啟自動列印。保持工作台頁面開啟；背景暫停、裝置休眠或斷線可能停止接單，需確認紙本後人工補印。

已完成前端語法及模擬檢查：Windows／USB 既有傳送、SPP 寫入與失敗釋放、BLE UUID 驗證與分段寫入、斷線停印、Apple 手動模式。不代表已驗證所有印表機實機相容性。

參考：
- https://developer.chrome.com/docs/capabilities/bluetooth
- https://developer.chrome.com/blog/serial-over-bluetooth
- https://support.apple.com/zh-tw/109349
