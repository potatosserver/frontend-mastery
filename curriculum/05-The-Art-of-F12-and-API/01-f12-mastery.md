# 01. F12 掌控指南 (F12 Mastery)

在進入 API 開發之前，你必須先學會如何使用瀏覽器的「上帝模式」 $\rightarrow$ **開發者工具 (DevTools/F12)**。

專業前端工程師 50% 的時間是在寫代碼，另外 50% 的時間是在 F12 裡觀察代碼如何運行。如果你不會使用 DevTools，你就像是在黑暗中開車。

---

## 1. 元素檢查 (Elements Tab)

這是最常用的功能。你可以直接在瀏覽器中修改 HTML 結構和 CSS 樣式，且結果會立即反應在頁面上。

**⚡️ 實作技巧：**
- **即時修改**：選中一個元素 $\rightarrow$ 在右側 Styles 面板修改顏色 $\rightarrow$ 觀察變化。
- **強制狀態**：右擊元素 $\rightarrow$ `Force state` $\rightarrow$ `:hover` $\rightarrow$ 檢查滑鼠懸停效果。

---

## 2. 控制台 (Console Tab)

Console 是你的「實驗場」。你可以在這裡直接執行 JS 代碼，或者觀察程式拋出的錯誤。

**🚀 專業操作：**
- **快速測試**：直接在 Console 寫 `alert("Hello")` 或 `console.log(window.innerWidth)`。
- **抓取數據**：使用 `document.querySelectorAll('.class')` 快速確認選取到了多少個元素。

---

## 3. 網路監控 (Network Tab)

這是 API 開發的靈魂。它記錄了瀏覽器與伺服器之間的所有通訊。

**⚡️ 必看指標：**
- **Status (狀態碼)**：`200` (成功), `404` (找不到), `500` (伺服器崩潰)。
- **Payload (請求參數)**：檢查發送給伺服器的數據是否正確。
- **Response (回應數據)**：查看伺服器回傳的 JSON 數據格式 $\rightarrow$ 這是寫 JS 邏輯的基礎。

---

## 🛠️ 實作挑戰

請打開任何一個你喜歡的網站（例如 Google 或 GitHub），執行以下操作：

1. **修改標題**：使用 Elements Tab 將頁面的 `<h1>` 文字改成你的名字。
2. **測試 API**：切換到 Network Tab $\rightarrow$ 刷新頁面 $\rightarrow$ 找到一個類型為 `fetch` 或 `xhr` 的請求 $\rightarrow$ 查看它的 Response。
3. **Console 計算**：在 Console 中執行 `2**10` (計算 2 的 10 次方)。

---
<p align="center">
<a href="../04-JS-Mastery/07-engine-and-event-loop.md">第7 engine and event loop ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/f12/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-api-sourcing-official.md">02-api-sourcing-official ➡️</a>
</p>
