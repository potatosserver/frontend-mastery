# 01. 工具鏈與開發環境 (Tooling & Dev Environment)

如果你仍然在使用單個 HTML 檔案搭配 `<script>` 標籤來開發，那你還在用 2010 年的方式工作。現代前端工程的核心不是「寫代碼」，而是 **「構建工具鏈 (Build Toolchain)」**。

---

## 📜 起源：為什麼我們需要構建工具？

在早期，JS 只需要瀏覽器執行即可。但隨著框架 (React/Vue) 和語言 (TS) 的出現，瀏覽器無法直接讀取這些代碼 $\rightarrow$ 我們需要一個 **「翻譯官」 (Compiler/Bundler)**。

- **Webpack (老牌巨頭)**：功能強大，但配置極其複雜 (Config Hell)，啟動速度慢 $\rightarrow$ 適合極大規模的舊專案。
- **Vite (現代標準)**：利用瀏覽器的原生 ES Modules (ESM) $\rightarrow$ **秒級啟動** $\rightarrow$ 極速熱更新 (HMR) $\rightarrow$ 目前所有新專案的首選。

---

## 1. 視覺化工作流：從代碼到瀏覽器的旅程

**🚀 專業開發流程：**
`撰寫 TS/JSX 代碼` $\rightarrow$ `Vite 實時翻譯 (Transform)` $\rightarrow$ `瀏覽器接收 ESM 模塊` $\rightarrow$ `畫面即時更新`。

**⚡️ 核心工具對比：**
- **npm / pnpm / yarn**：包管理器 $\rightarrow$ 負責管理第三方庫 (如 Axios, Lodash) $\rightarrow$ 建議使用 `pnpm` $\rightarrow$ 節省硬碟空間且速度最快。
- **ESLint** $\rightarrow$ 靜態分析工具 $\rightarrow$ 在你提交代碼前就告訴你：「這裡少了一個分號」或「這個變數沒被使用」 $\rightarrow$ 確保團隊代碼風格統一。
- **Prettier** $\rightarrow$ 代碼格式化工具 $\rightarrow$ 按下 `Ctrl+S` $\rightarrow$ 自動把凌亂的代碼排版成工業級標準。

---

## 2. 實作挑戰：建立你的現代開發環境

請在你的本地環境嘗試以下操作：

1. **快速啟動 Vite** $\rightarrow$ 執行 `npm create vite@latest` $\rightarrow$ 選擇 `Vanilla` $\rightarrow$ `TypeScript` $\rightarrow$ 觀察啟動速度。
2. **配置 ESLint $\rightarrow$ Prettier** $\rightarrow$ 安裝相關插件 $\rightarrow$ 嘗試寫一段格式混亂的代碼 $\rightarrow$ 觀察保存後自動對齊的過程。
3. **分析 `node_modules`** $\rightarrow$ 嘗試安裝一個大型庫 $\rightarrow$ 觀察 `package-lock.json` 的作用 $\rightarrow$ 理解為什麼不能把 `node_modules` 上傳到 Git。

---
<p align="center">
<a href="../09-Modern-Framework-Architecture/05-advanced-deployment.md">第5 advanced deployment ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/qa/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-testing-pyramid.md">02-testing-pyramid ➡️</a>
</p>
