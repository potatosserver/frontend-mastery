# 04. CORS 與代理伺服器 (CORS and Proxy)

當你嘗試在自己的網站中使用逆向工程找到的 API 時，你幾乎 100% 會遇到一個恐怖的紅字錯誤 $\rightarrow$ **CORS Error (跨來源資源共用錯誤)**。

---

## 1. 什麼是 CORS？ (Cross-Origin Resource Sharing)

這不是 JS 的 Bug，而是瀏覽器為了保護使用者而設定的 **安全機制**。

**邏輯是這樣的：**
- 瀏覽器發現你要從 `domain-a.com` (你的網站) 請求 `domain-b.com` (伺服器) 的數據。
- 瀏覽器會問伺服器：「嘿，你允許 `domain-a.com` 拿你的數據嗎？」
- 如果伺服器沒在 Header 中寫 `Access-Control-Allow-Origin: *` $\rightarrow$ 瀏覽器會直接攔截結果 $\rightarrow$ 拋出 CORS 錯誤。

---

## 2. 解決方案：代理伺服器 (Proxy Server)

前端開發者無法強迫他人修改伺服器設定。解決方案就是 **「繞道」**。

**路徑對比：**
- **❌ 直接請求**：`瀏覽器 (A) $\rightarrow$ 伺服器 (B)` $\rightarrow$ 觸發 CORS 攔截。
- **✅ 使用代理**：`瀏覽器 (A) $\rightarrow$ 自己的代理伺服器 (C) $\rightarrow$ 伺服器 (B)`。

**為什麼有效？**
因為 **CORS 限制只存在於「瀏覽器」中**。伺服器與伺服器之間的通訊（例如 Node.js 請求 API）是不受 CORS 限制的。

---

## 3. 實作工具：CORS AnyWhere 與 自建代理

- **臨時方案**：使用像 `cors-anywhere` 這樣的公共代理服務 $\rightarrow$ 在 API URL 前加上代理前綴。
- **專業方案**：使用 Node.js + Express 建立一個簡單的代理後端 $\rightarrow$ 接收前端請求 $\rightarrow$ 在後端抓取數據 $\rightarrow$ 回傳給前端。

---

## 🛠️ 實作挑戰

1. **觸發 CORS 錯誤**：嘗試在 JS 中 `fetch` 一個隨機的官方網站（如 google.com），觀察 Console 裡的紅字錯誤。
2. **測試代理**：尋找一個公開的 CORS 代理伺服器 $\rightarrow$ 嘗試請求同樣的接口 $\rightarrow$ 確認數據成功回傳。
3. **分析 Header**：在 Network Tab 查看請求頭 $\rightarrow$ 尋找 `Origin` 與 `Access-Control-Allow-Origin`。

---
<p align="center">
<a href="03-api-reverse-engineering.md">03-api-reverse-engineering ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/f12/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../06-Browser-Capabilities/01-dom-performance.md">01-dom-performance ➡️</a>
</p>
