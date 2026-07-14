# 03. API 逆向工程 (API Reverse Engineering)

很多網站並沒有提供官方 API $\rightarrow$ 但它們仍然在後端獲取數據並顯示在頁面上。這時候，專業工程師會使用 **逆向工程 (Reverse Engineering)** 找出它們私下使用的「隱藏接口」。

---

## 1. 核心邏輯：數據從哪來？

瀏覽器顯示的任何動態內容 $\rightarrow$ 必然經過一次網路請求。

**🚀 挖掘步驟：**
1. 打開 F12 $\rightarrow$ 切換到 **Network** 標籤。
2. 選擇 `Fetch/XHR` 過濾器 $\rightarrow$ 排除圖片和 CSS。
3. 執行頁面操作 (例如：點擊「加載更多」) $\rightarrow$ 觀察新出現的請求。
4. 點擊請求 $\rightarrow$ 查看 `Response` $\rightarrow$ 如果看到 JSON 數據，恭喜你找到了！

---

## 2. 分析請求構造 (Request Analysis)

找到接口後，你需要分析它是如何被呼叫的：
- **URL**：接口的正確路徑。
- **Method**：是 `GET` (獲取數據) 還是 `POST` (提交數據)。
- **Headers**：有沒有特殊的 `Authorization` 或 `User-Agent` 要求。
- **Query Params**：URL 後面的 `?page=1&limit=10` 是如何控制數據的。

---

## 3. 法律與道德紅線 (Ethics & Legal)

逆向工程是一個強大但危險的工具。
- **禁止行為**：對伺服器進行高頻率請求 (DoS 攻擊)、繞過支付牆獲取私有數據。
- **正確做法**：僅用於學習研究，或在合理範圍內獲取公開數據 $\rightarrow$ 尊重 `robots.txt` 協議。

---

## 🛠️ 實作挑戰

1. **挖掘接口**：找一個新聞網站 $\rightarrow$ 在 Network Tab 中找到它獲取新聞列表的接口。
2. **模擬請求**：使用 `fetch()` 在 Console 中嘗試呼叫該接口 $\rightarrow$ 確認能拿到一樣的 JSON 數據。
3. **分析參數**：嘗試修改請求中的 `page` 參數 $\rightarrow$ 觀察回傳的數據是否變成了第二頁。

---
<p align="center">
<a href="02-api-sourcing-official.md">02-api-sourcing-official ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/f12/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-cors-and-proxy.md">04-cors-and-proxy ➡️</a>
</p>
