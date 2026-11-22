# Windows USB 自動出單

適用於已安裝 CP-Q1UN／PrinterPOS-80 Windows 驅動的電腦。透過 Windows 印表機佇列傳送 ESC/POS 點陣資料，保留中文，不使用 Chrome WebUSB。

1. 下載 `windows-print-bridge.ps1` 至電腦。
2. 在檔案所在資料夾開啟 PowerShell，執行：

   `powershell -NoProfile -ExecutionPolicy Bypass -File .\windows-print-bridge.ps1`

3. 在程式視窗輸入 CP-Q1UN 的編號，保持視窗開啟。
4. 開啟湯達人廚房／前台，按「連接 USB 印表機」，貼上程式顯示的 Pairing code。Chrome 若詢問本機／區域網路存取，選允許。
5. 按「測試列印」。出紙正常後，勾選「收到訂單自動列印」。廚房接收新點餐單，前台接收結帳清單。

只在一台對應工作台啟用自動列印。啟用時會接收尚未處理的待印工作，包含舊待印單。

程式只監聽 127.0.0.1:17888，要求指定網站來源及每次啟動產生的配對碼，不需要更換 Windows USB 驅動。配對碼只存於當前瀏覽器工作階段。關閉程式後停止服務；重啟需重新配對。

傳送結果表示 Windows 佇列已接受，仍需確認紙本。斷線或部分出紙後請確認紙本再人工補印。程式以本機紀錄避免同一工作因網路重試再次傳送；不會自動重送狀態不明的工作。

已完成網頁腳本語法、權限、路由及列印傳送模擬檢查；Windows PowerShell 編譯啟動、CP-Q1UN 實機出紙仍需在使用電腦驗證。
