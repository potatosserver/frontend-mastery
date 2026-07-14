# 02. 測試金字塔 (The Testing Pyramid)

很多初學者認為測試就是「手動打開網頁 $\rightarrow$ 點一遍 $\rightarrow$ 沒報錯就完事」 $\rightarrow$ 這在專業工程領域被稱為 **「隨機測試」** $\rightarrow$ 它是最不可靠的。

為了確保產品在更新後不會崩潰 $\rightarrow$ 我們必須建立 **「測試金字塔 (Testing Pyramid)」**。

---

## 📜 起源：為什麼需要金字塔？

如果你所有的測試都依賴於打開瀏覽器 $\rightarrow$ 運行一次完整測試可能需要 2 小時 $\rightarrow$ 工程師會因為太慢而放棄測試。
金字塔的核心理念是：**用最快、最廉價的測試覆蓋最多邏輯，用最慢、最昂貴的測試驗證核心流程。**

---

## 1. 視覺化分層：金字塔的三層結構

### 底層：單元測試 (Unit Tests) $\rightarrow$ 「零件檢查」
- **目標**：測試單個函數或組件的邏輯 $\rightarrow$ 例如：`calculateTotal(10, 2)` 是否正確回傳 `12`。
- **特點**：**極速** $\rightarrow$ 毫秒級執行 $\rightarrow$ 數量最多。
- **工具**：`Vitest`, `Jest`。

### 中層：集成測試 (Integration Tests) $\rightarrow$ 「模組接合」
- **目標**：測試多個組件協同工作的流程 $\rightarrow$ 例如：`輸入用戶名 $\rightarrow$ 點擊登入 $\rightarrow$ 驗證是否跳轉至首頁`。
- **特點**：速度中等 $\rightarrow$ 數量適中。

### 頂層：端到端測試 (E2E Tests) $\rightarrow$ 「用戶旅程」
- **目標**：模擬真實用戶在瀏覽器中的行為 $\rightarrow$ 驗證完整業務鏈條。
- **特點**：**最慢** $\rightarrow$ 成本最高 $\rightarrow$ 數量最少。
- **工具**：`Playwright`, `Cypress`。

---

## 2. 專業實作：如何撰寫一個高品質的測試？

一個好的測試必須遵循 **AAA 模式**：
1. **Arrange (準備)** $\rightarrow$ 設定測試所需的數據 (例如：創建一個虛擬用戶)。
2. **Act (執行)** $\rightarrow$ 呼叫要測試的函數或觸發點擊事件。
3. **Assert (驗證)** $\rightarrow$ 使用 `expect().toBe()` 驗證結果是否符合預期。

**🚀 實作對比：**
- **❌ 糟糕的測試**：`test('it works', () => { run(); })` $\rightarrow$ 只要沒崩潰就通過 $\rightarrow$ 毫無意義。
- **✅ 專業測試**：`test('should return error when price is negative', () => { expect(calc(-10)).toBe('Invalid Price'); })` $\rightarrow$ 精確定義邊界條件。

---

## 🛠️ 測試實作挑戰

1. **實作單元測試** $\rightarrow$ 為你的 `05-TS` 模組中的 `calculateTotal` 函數編寫 3 個測試案例 $\rightarrow$ 包含正常情況與邊界情況 (如：負數, 空字串)。
2. **設計測試矩陣** $\rightarrow$ 針對你的作品集網站 $\rightarrow$ 列出 5 個必須進行 E2E 測試的核心流程 (例如：聯絡表單提交)。
3. **實作 Mocking** $\rightarrow$ 學習如何使用 `vi.fn()` 模擬 API 回傳 $\rightarrow$ 在沒有伺服器的情況下測試前端的錯誤處理邏輯。

---
<p align="center">
<a href="01-tooling-vite-npm.md">01-tooling-vite-npm ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/qa/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-jest-cypress-play.md">03-jest-cypress-play ➡️</a>
</p>
