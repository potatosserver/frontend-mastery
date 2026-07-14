# 03. 實戰測試工具 (Practical Testing Tools)

在理解了測試金字塔之後，我們需要將理論轉化為工具。現代前端工程師的武器庫中，最核心的三件武器是：**Vitest, Playwright 與 Cypress**。

---

## 📜 起源：為什麼不再使用 Selenium？

早期的 E2E 測試依賴 Selenium $\rightarrow$ 它像是一個「遠程控制的機器人」 $\rightarrow$ 速度極慢 $\rightarrow$ 經常因為網路波動而隨機失敗 (Flaky Tests)。

現代工具如 **Playwright (微軟)** 與 **Cypress** 則直接與瀏覽器的 CDP (Chrome DevTools Protocol) 通訊 $\rightarrow$ 實現了 **「毫秒級同步」** $\rightarrow$ 讓測試像跑 JS 腳本一樣快。

---

## 1. 工具鏈選擇指南

根據金字塔的不同層級，選擇對應的武器：

### A. 單元測試 $\rightarrow$ Vitest / Jest
- **核心功能**：高速執行-快照測試 (Snapshot Testing)- Mocking。
- **專業技巧**：使用 **快照測試** $\rightarrow$ 將組件的 HTML 結構存為檔案 $\rightarrow$ 每次更新後對比 $\rightarrow$ 只要有一個標籤變了，測試立刻報錯 $\rightarrow$ 防止視覺回退 (Regression)。

### B. E2E 測試 $\rightarrow$ Playwright / Cypress
- **核心功能**：自動化操作-截圖錄製-跨瀏覽器驗證。
- **專業技巧**：使用 **自動等待 (Auto-waiting)** $\rightarrow$ 只要元素還沒出現，工具會自動等待 $\rightarrow$ 消除 `sleep(3000)` 這種低效寫法。

---

## 2. 實作：撰寫第一個 E2E 測試

想像你要測試「聯絡表單」是否能正常運作。

**🚀 專業測試路徑：**
```javascript
test('should submit contact form successfully', async ({ page }) => {
    await page.goto('/contact');
    await page.fill('#name', 'Andrew');
    await page.fill('#email', 'test@example.com');
    await page.click('#submit');
    
    // 驗證是否出現成功提示
    await expect(page.locator('.success-msg')).toBeVisible();
});
```

---

## 🛠️ 工具實作挑戰

1. **實作快照測試** $\rightarrow$ 使用 Vitest 為你的 M3 作品卡片撰寫快照測試 $\rightarrow$ 嘗試修改 CSS $\rightarrow$ 觀察快照如何報錯。
2. **打造自動化冒煙測試 (Smoke Test)** $\rightarrow$ 使用 Playwright 編寫一個腳本 $\rightarrow$ 自動開啟瀏覽器 $\rightarrow$ 依次點擊所有導航按鈕 $\rightarrow$ 驗證所有頁面均能正常載入 (無 404)。
3. **分析測試覆蓋率 (Coverage)** $\rightarrow$ 運行 `vitest --coverage` $\rightarrow$ 查看哪些代碼還沒有被測試覆蓋 $\rightarrow$ 針對弱點補齊單元測試。

---
<p align="center">
<a href="02-testing-pyramid.md">02-testing-pyramid ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/qa/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-git-and-ci-cd.md">04-git-and-ci-cd ➡️</a>
</p>
