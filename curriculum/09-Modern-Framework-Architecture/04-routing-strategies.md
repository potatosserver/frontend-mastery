# 04. 路由策略 (Routing Strategies)

如果你的網站只有一個頁面 $\rightarrow$ 那是單頁應用 (Single Page Application, SPA)。但如果你的網站有「首頁」、「關於」、「作品集」、「聯絡我」 $\rightarrow$ 你需要一套 **路由系統 (Routing System)** 來管理 URL。

---

## 📜 起源：從伺服器路由到客戶端路由

**舊時代 (Server-Side Routing)：**
每次點擊連結 $\rightarrow$ 瀏覽器發送請求 $\rightarrow$ 伺服器返回整個新 HTML 頁面 $\rightarrow$ 瀏覽器刷新 $\rightarrow$ **視覺閃爍 (Flicker)** $\rightarrow$ 體驗極差。

**新時代 (Client-Side Routing)：**
瀏覽器只下載一次 HTML $\rightarrow$ 當 URL 改變時 $\rightarrow$ JS 攔截請求 $\rightarrow$ **只替換頁面中的部分內容** $\rightarrow$ 無需刷新 $\rightarrow$ 體感速度極快。

---

## 1. 路由的兩種核心模式

### A. Hash 路由 (`/#/about`)
- **原理**：使用 URL 中的 `#` 號 $\rightarrow$ 瀏覽器不會將 `#` 後的內容發送到伺服器 $\rightarrow$ 實作最簡單 $\rightarrow$ 不需要伺服器配置。
- **缺點**：URL 醜陋 $\rightarrow$ 對 SEO 不友善。

### B. History 路由 (`/about`)
- **原理**：使用 HTML5 的 `history.pushState` API $\rightarrow$ 模擬真實 URL。
- **缺點**：需要伺服器配置 (所有請求都指向 `index.html`) $\rightarrow$ 否則刷新頁面會出現 404。

---

## 2. 專業路由設計：動態路由與守衛 (Guards)

專業產品不會只寫死幾個頁面，而是使用 **動態路由 (Dynamic Routing)**。

**🚀 實作場景：作品詳情頁**
你不需要為 100 個作品寫 100 個頁面 $\rightarrow$ 只寫一個模板 $\rightarrow$ 使用路徑參數：
`/projects/:id` $\rightarrow$ JS 根據 `:id` 從 API 抓取數據 $\rightarrow$ 填充到模板中。

**🛡️ 路由守衛 (Route Guards) $\rightarrow$ 權限控制：**
在進入頁面之前，先執行一段邏輯 $\rightarrow$ 例如：
`if (!isLoggedIn) { redirect('/login'); }` $\rightarrow$ 防止未登入使用者進入管理後台。

---

## 🛠️ 路由實作挑戰

1. **建立簡單路由表** $\rightarrow$ 在 JS 中定義一個對象 `{ '/about': AboutComponent, '/work': WorkComponent }` $\rightarrow$ 監聽 `popstate` 事件 $\rightarrow$ 根據 URL 渲染對應組件。
2. **實作動態路徑** $\rightarrow$ 建立 `/project/:id` 路由 $\rightarrow$ 嘗試通過 URL 傳遞 ID $\rightarrow$ 在頁面上顯示「您正在查看第 [ID] 個作品」。
3. **設計導航高亮** $\rightarrow$ 監聽當前路徑 $\rightarrow$ 當路徑與導航按鈕匹配時 $\rightarrow$ 給按鈕加上 `.active` 類名。

---
<p align="center">
<a href="03-component-patterns.md">03-component-patterns ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/framework/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="05-advanced-deployment.md">05-advanced-deployment ➡️</a>
</p>
