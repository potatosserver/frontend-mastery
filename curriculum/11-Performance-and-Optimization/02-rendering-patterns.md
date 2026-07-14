# 02. 渲染模式對比 (Rendering Patterns)

如果你把所有東西都放在一個大的 JS 檔案裡 $\rightarrow$ 瀏覽器必須下載 $\rightarrow$ 解析 $\rightarrow$ 執行 $\rightarrow$ 才能看到內容 $\rightarrow$ 這就是傳統的 **CSR (客戶端渲染)**。但對於專業產品，這太慢了。

為了在「速度」與「動態功能」之間取得平衡 $\rightarrow$ 業界演進出了四種渲染模式。

---

## 📜 起源：從靜態到動態的演進

早期的網頁是 **靜態 (Static)** 的 $\rightarrow$ 伺服器直接給 HTML $\rightarrow$ 極快但不能互動。
後來有了 **CSR (Client-Side Rendering)** $\rightarrow$ 讓網頁像 App 一樣流暢，但首屏加載太慢 $\rightarrow$ 對 SEO 極其不友善。

為了修復這個缺陷 $\rightarrow$ 誕生了 **SSR (伺服器端渲染)** 與 **SSG (靜態網站生成)**。

---

## 1. 視覺化對比：四種渲染模式

| 模式 | 運作方式 | 優點 | 缺點 | 適用場景 |
| :--- | :--- | :--- | :--- | :--- |
| **CSR** | 瀏覽器執行 JS $\rightarrow$ 畫出內容 | 互動流暢-無刷新感 | 首屏慢-SEO 差 | 管理後台-內部工具 |
| **SSR** | 伺服器即時生成 HTML $\rightarrow$ 回傳 | 首屏極快-SEO 極佳 | 伺服器壓力大-開發複雜 | 電商主頁-新聞網站 |
| **SSG** | 構建時預先生成 HTML 檔案 | 速度最快-最安全 | 內容更新需重新構建 | 博客-文檔-作品集 |
| **ISR** | 定時在背景更新部分靜態頁面 | 兼顧速度與實時性 | 實現複雜 | 大型內容平台 |

---

## 2. 實作：如何為你的作品集選擇模式？

**🚀 專業建議：**
對於個人作品集 $\rightarrow$ **SSG (靜態生成)** 是唯一正確的選擇。
- **原因**：你的作品內容不會每秒鐘改變 $\rightarrow$ 預先生成 HTML 可以讓使用者在 0.1 秒內看到內容 $\rightarrow$ 且對 Google 搜尋極其友好。

**⚡️ 實作路徑：**
1. 使用 **Next.js** 或 **Nuxt.js** $\rightarrow$ 配置 `output: 'export'`。
2. 將生成的 `out/` 或 `dist/` 資料夾部署到 Vercel/Netlify。
3. 觀察 LCP 指標 $\rightarrow$ 發現首屏加載幾乎是瞬間完成。

---

## 🛠️ 渲染模式挑戰

1. **分析對比** $\rightarrow$ 找一個 CSR 網站 (例如早期的 Gmail) 與一個 SSG 網站 (例如 Vercel 官網) $\rightarrow$ 查看頁面原始碼 $\rightarrow$ 觀察一個有內容 vs 一個只有 `<div id="app"></div>`。
2. **實作簡單 SSR** $\rightarrow$ 使用 Node.js + Express $\rightarrow$ 嘗試在伺服器端拼接 HTML 字串並回傳 $\rightarrow$ 觀察 F12 Network Tab $\rightarrow$ 確認 HTML 內容直接出現在 Response 中。
3. **設計混合模式** $\rightarrow$ 思考：如果你的作品集需要一個「即時聊天」功能 $\rightarrow$ 你該用哪種模式？ (答案：SSG 頁面 + CSR 組件)。

---
<p align="center">
<a href="01-web-vitals.md">01-web-vitals ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/perf/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-bundle-optimization.md">03-bundle-optimization ➡️</a>
</p>
