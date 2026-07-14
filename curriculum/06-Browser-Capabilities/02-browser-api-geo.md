# 02. 瀏覽器 API 與地理位置實作 (Browser API & Geo)

現代瀏覽器不再只是顯示文件的工具 $\rightarrow$ 它是一個功能強大的 **操作系統**。它可以訪問你的相機、麥克風、加速度計，以及最重要的 $\rightarrow$ **地理位置 (Geolocation)**。

---

## 📜 起源：從「靜態頁面」到「環境感知」

早期的網頁是死的 $\rightarrow$ 它不知道你在哪，也不知道你的設備是什麼。
隨著行動互聯網的興起，Google 和 W3C 推出了 **Web API** 規範 $\rightarrow$ 讓網頁能感知使用者的「物理環境」。

**專業工程師的思考 $\rightarrow$ 權限管理 (Permissions)：**
由於隱私問題，瀏覽器不會直接給你數據 $\rightarrow$ 你必須先請求 **使用者授權 (User Consent)**。

---

## 1. 視覺化目標：實作「附近的作品展」功能

想像你的作品集網站能根據使用者的位置 $\rightarrow$ 推薦最近的合作夥伴或實體展覽。

**🚀 實作路徑：**
1. **請求授權** $\rightarrow$ 呼叫 `navigator.geolocation.getCurrentPosition()`。
2. **處理座標** $\rightarrow$ 獲取 `latitude` (緯度) 與 `longitude` (經度)。
3. **對接地圖** $\rightarrow$ 將座標傳給 Google Maps 或 OpenStreetMap API。

**⚡️ 專業代碼實作：**
```javascript
navigator.geolocation.getCurrentPosition(
    (position) => {
        const { latitude, longitude } = position.coords;
        console.log(`你在這裡: ${latitude}, ${longitude}`);
        // 這裡可以調用地圖 API 顯示標記
    },
    (error) => {
        console.error("授權失敗:", error.message);
        alert("請開啟位置權限以獲取附近推薦");
    }
);
```

---

## 2. 進階：實時追蹤 (Watch Position)

如果你在做一個「跑步紀錄」或「外送追蹤」功能 $\rightarrow$ 獲取一次位置是不夠的 $\rightarrow$ 你需要 **實時監控 (Watching)**。

**💡 實作要點：**
- 使用 `navigator.geolocation.watchPosition()`。
- **性能警告**：GPS 極其耗電 $\rightarrow$ 必須在不需要時使用 `clearWatch()` 關閉追蹤。

---

## 🛠️ 瀏覽器能力挑戰

1. **建立權限請求按鈕** $\rightarrow$ 點擊後請求位置授權 $\rightarrow$ 成功後在頁面上顯示：「您目前位於 [城市/座標]」。
2. **實作即時座標顯示** $\rightarrow$ 使用 `watchPosition` $\rightarrow$ 在頁面上創建一個滾動列表 $\rightarrow$ 每秒更新一次座標 $\rightarrow$ 觀察數值的微小變動。
3. **處理拒絕場景** $\rightarrow$ 當使用者拒絕權限時 $\rightarrow$ 顯示一個優雅的「備用方案 (Fallback)」提示 $\rightarrow$ 告訴使用者手動輸入城市。

---
<p align="center">
<a href="01-dom-performance.md">01-dom-performance ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/browser/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-web-storage-deep.md">03-web-storage-deep ➡️</a>
</p>
