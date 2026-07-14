# 02. 安全加固與加密 (Security Hardening)

如果你在處理使用者密碼、信用卡號或個人私隱 $\rightarrow$ 隨便使用 `fetch` 就是在幫駭客開後門。

在網路通訊中，安全不是一個「選項」，而是 **「底線」**。

---

## 📜 起源：從明文 (Plaintext) 到加密 (Encryption)

早期的 HTTP 是明文傳輸的 $\rightarrow$ 任何處於同一 WiFi 下的駭客，只要使用簡單的「封包監聽 (Packet Sniffing)」工具 $\rightarrow$ 就能直接看到你的密碼。

為了解決這個問題，業界推出了 **SSL/TLS** $\rightarrow$ 將 HTTP 升級為 **HTTPS**。HTTPS 的本質就是：**在傳輸數據前，先用數學加密。**

---

## 1. 必須掌握的安全機制

專業前端工程師必須在開發時考慮以下三道防線：

### A. HTTPS 與 TLS 握手
- **原理**：伺服器提供一個「數位證書」 $\rightarrow$ 瀏覽器驗證證書有效性 $\rightarrow$ 雙方協商出一個臨時的「對稱密鑰」進行加密通訊。
- **視覺表現**：瀏覽器地址欄的 **「鎖頭」** 圖標。

### B. XSS (跨站腳本攻擊) $\rightarrow$ 預防注入
- **攻擊方式**：駭客在留言板輸入 `<script>stealCookie()</script>` $\rightarrow$ 你的網頁直接執行了這段代碼 $\rightarrow$ 盜走使用者 Cookie。
- **防禦方案**：對所有使用者輸入進行 **「轉義 (Escaping)」** $\rightarrow$ 將 `<` 變成 `&lt;`，讓瀏覽器將其視為文字而非代碼。

### C. CSRF (跨站請求偽造) $\rightarrow$ 預防冒充
- **攻擊方式**：駭客誘導使用者點擊一個連結 $\rightarrow$ 該連結在後台悄悄向你的銀行 API 發送 `transfer_money` 請求 $\rightarrow$ 伺服器發現使用者已登入，於是執行了轉帳。
- **防禦方案**：使用 **CSRF Token** (隨機令牌) $\rightarrow$ 伺服器要求每個請求必須攜帶正確的 Token，否則拒絕執行。

---

## 2. 實作：安全 Headers 配置

如果你負責部署網站，必須在伺服器配置中加入 **CSP (Content Security Policy)**。

**🚀 專業配置範例：**
```http
Content-Security-Policy: default-src 'self'; script-src 'self' https://trusted.com;
```
這行指令告訴瀏覽器：「除非是來自我自己或 trusted.com 的腳本，否則全部禁止執行」 $\rightarrow$ 徹底根除 XSS 攻擊。

---

## 🛠️ 安全實作挑戰

1. **分析不安全網站** $\rightarrow$ 找一個僅使用 `http://` 的舊網站 $\rightarrow$ 觀察瀏覽器顯示的「不安全」警告。
2. **實作 XSS 漏洞演示** $\rightarrow$ 建立一個簡單的輸入框 $\rightarrow$ 嘗試輸入 `<img src=x onerror=alert(1)>` $\rightarrow$ 觀察是否彈出視窗 $\rightarrow$ 接著實作「轉義函數」來修復它。
3. **研究 CSP 策略** $\rightarrow$ 嘗試在自己的網站加入 CSP Header $\rightarrow$ 刻意引入一個第三方不信任的腳本 $\rightarrow$ 在 F12 Console 觀察 CSP 攔截的紅字錯誤。

---
<p align="center">
<a href="01-http-deep-dive.md">01-http-deep-dive ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/net/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-rest-vs-graphql.md">03-rest-vs-graphql ➡️</a>
</p>
