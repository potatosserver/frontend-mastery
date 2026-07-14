# 04. Git 與 CI/CD 實戰 (Git & CI/CD Practical)

如果你只會 `git add .` $\rightarrow$ `git commit -m "fix"` $\rightarrow$ `git push` $\rightarrow$ 那你只是在使用 Git 作為「備份工具」。專業工程師使用 Git 來進行 **「版本控制與團隊協作」**。

---

## 📜 起源：從單人開發到團隊工業化

在沒有 Git 的時代 $\rightarrow$ 協作方式是 `project_v1.zip`, `project_v2_final.zip`, `project_v2_final_really_final.zip` $\rightarrow$ 這簡直是災難。

Git 引入了 **「分支 (Branching)」** 與 **「合併 (Merging)」** $\rightarrow$ 讓 100 個工程師可以同時修改同一份代碼 $\rightarrow$ 且在最後將所有變更安全地整合在一起。

---

## 1. 專業 Git 工作流：Git Flow 與 Feature Branch

不要直接在 `main` 分支提交代碼。專業團隊遵循 **Feature Branch 工作流**：

**🚀 實作路徑：**
1. **建立分支** $\rightarrow$ `git checkout -b feature/new-card-style`。
2. **開發與提交** $\rightarrow$ 撰寫代碼 $\rightarrow$ 提交到分支。
3. **發起 PR (Pull Request)** $\rightarrow$ 在 GitHub 上提交請求 $\rightarrow$ 邀請同事 Review 代碼。
4. **合併分支** $\rightarrow$ Review 通過 $\rightarrow$ 合併至 `main` $\rightarrow$ 刪除特性分支。

---

## 2. 實作 CI/CD：將測試自動化

將 Git 與測試工具結合 $\rightarrow$ 建立自動化門禁。

**⚡️ 專業管線邏輯：**
`Git Push` $\rightarrow$ `觸發 GitHub Action` $\rightarrow$ `運行 Vitest 單元測試` $\rightarrow$ `運行 Playwright E2E 測試` $\rightarrow$ **如果其中一個失敗 $\rightarrow$ 拒絕合併 $\rightarrow$ 阻止部署**。

這確保了你的生產環境永遠是 **「經過驗證的正確版本」**。

---

## 3. 實作挑戰：模擬一次工業級協作

1. **實作分支管理** $\rightarrow$ 為你的主專案建立一個 `feature/footer-update` 分支 $\rightarrow$ 在分支中修改頁尾 $\rightarrow$ 切回 `main` 分支 $\rightarrow$ 觀察代碼的切換。
2. **撰寫專業提交訊息 (Commit Message)** $\rightarrow$ 遵循 `Conventional Commits` 規範 $\rightarrow$ 例如：`feat(ui): add m3-style floating button` 或 `fix(net): resolve cors issue in API`。
3. **配置 Git 忽略 (gitignore)** $\rightarrow$ 建立 `.gitignore` $\rightarrow$ 確保 `node_modules`, `.env`, `dist/` 等垃圾檔案不會被提交到倉庫。

---
<p align="center">
<a href="03-jest-cypress-play.md">03-jest-cypress-play ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/qa/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../11-Performance-and-Optimization/01-web-vitals.md">01-web-vitals ➡️</a>
</p>
