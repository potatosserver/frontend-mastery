# 05. 進階部署與 CI/CD (Advanced Deployment & CI/CD)

當你的作品集網站開發完成後，它還只是存在於你電腦上的 `localhost`。要讓全世界看到它，你需要將其 **部署 (Deployment)** 到伺服器上。

但專業工程師不會用 FTP 手動上傳檔案 $\rightarrow$ 他們使用 **CI/CD (持續整合 / 持續部署)** 流程。

---

## 📜 起源：從「手動上傳」到「自動化管線」

在早期的開發模式中，部署過程是這樣的：
`本地修改代碼` $\rightarrow$ `壓縮成 ZIP` $\rightarrow$ `登錄 FTP` $\rightarrow$ `覆蓋伺服器檔案` $\rightarrow$ `刷新頁面驗證`。
這導致了兩個巨大的問題：
1. **人為錯誤**：漏掉一個檔案 $\rightarrow$ 網站直接崩潰。
2. **效率低下**：每次小修改都要重複上述流程 $\rightarrow$ 浪費時間。

**CI/CD (Continuous Integration / Continuous Deployment)** 的出現改變了這一切 $\rightarrow$ 它將部署變成了一條 **「自動化生產線」**。

---

## 1. CI/CD 運作流程：自動化管線 (Pipeline)

現代的前端部署流程通常如下：

**🚀 流程圖：**
`Git Push (提交代碼)` $\rightarrow$ `GitHub Actions (觸發管線)` $\rightarrow$ `Install (安裝依賴)` $\rightarrow$ `Lint & Test (檢查錯誤)` $\rightarrow$ `Build (編譯 TS/框架)` $\rightarrow$ `Deploy (自動推送至 Vercel/Netlify)`。

**💡 核心價值：**
- **自動化測試**：如果代碼有 Bug $\rightarrow$ 測試失敗 $\rightarrow$ 管線直接停止 $\rightarrow$ 確保崩潰的代碼永遠不會到達生產環境。
- **原子部署 (Atomic Deploy)**：新版本完全準備好後，才瞬間切換 $\rightarrow$ 使用者感受不到部署過程。

---

## 2. 實作方案：選擇你的部署平台

現在有許多專為前端設計的 **Serverless 部署平台**，讓你可以實現 「Push 即可部署」。

| 平台 | 特點 | 推薦場景 |
| :--- | :--- | :--- |
| **Vercel** | Next.js 官方平台-極速-完美整合 | 追求極速部署-現代框架專案 |
| **Netlify** | 強大的 Edge Functions-簡單易用 | 靜態網站-小型作品集 |
| **GitHub Pages** | 完全免費-與 Repo 深度綁定 | 簡單的個人主頁-開源專案 |

---

## 3. 實作挑戰：建立你的自動化管線

1. **配置 GitHub Action** $\rightarrow$ 在專案中建立 `.github/workflows/deploy.yml` $\rightarrow$ 實作「每次 Push 到 main 分支時自動運行 `npm run build`」。
2. **實作 Lint 檢查** $\rightarrow$ 將 `eslint` 納入 CI 管線 $\rightarrow$ 如果代碼不符合規範 $\rightarrow$ 拒絕合併 (Merge) 請求。
3. **部署至 Vercel/Netlify** $\rightarrow$ 將你的 GitHub 倉庫連結到平台 $\rightarrow$ 體驗一次「提交代碼 $\rightarrow$ 自動部署 $\rightarrow$ 獲得正式 URL」的全過程。

---
<p align="center">
<a href="04-routing-strategies.md">04-routing-strategies ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/framework/05-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../10-Engineering-and-QA/01-tooling-vite-npm.md">01-tooling-vite-npm ➡️</a>
</p>
