# 熱量累積計算器（Android）

第一版功能：
- 設定每小時消耗熱量。
- 依開始計算的時間戳記補算已經過的完整小時，App 關閉期間不會漏算。
- 可設定早餐、午餐、晚餐的自動扣除時間與熱量；每天每餐只扣一次。
- 可手動正負調整。
- 資料保存在手機本機 SharedPreferences。

## 用 GitHub Actions 編譯 APK
1. 在 GitHub 建立一個空白 repository。
2. 將本專案所有檔案上傳到 repository 根目錄（包含 `.github/workflows/build-apk.yml`）。
3. 開啟 repository 的 **Actions** 頁面，選擇 **Build Android APK**，按 **Run workflow**。
4. 工作完成後，在該次執行頁面底部的 **Artifacts** 下載 `calorie-accumulator-debug-apk`。
5. 解壓縮後取得 `app-debug.apk`，傳到 Android 手機安裝。若手機詢問，允許該來源安裝未知應用程式。

## 注意
- 本版以時間戳記計算，不依賴背景常駐服務，因此關閉 App 後仍可補算完整小時；畫面會在下次開啟時更新。
- 用餐扣除會在 App 開啟時檢查；若跨過設定時間而 App 關閉，重新開啟後會補登當天該餐一次。
- 第一版不含雲端同步、通知或健康平台整合。
- 目前為 debug APK，適合個人測試，不是正式上架簽署版本。
