# 01. 框架哲學 (Framework Philosophy)

在學習具體的框架（如 React, Vue, 或 Svelte）之前，你必須先理解一個核心問題：**既然我們已經可以用純 JS (Vanilla JS) 做所有事，為什麼還要引入一個沉重的框架？**

---

## 📜 起源：從「手動操作」到「聲明式 UI」

在純 JS 時代，我們使用的是 **「指令式 (Imperative)」** 思考模式 $\rightarrow$ 告訴瀏覽器「怎麼做」。
**範例**：我要先找到那個按鈕 $\rightarrow$ 監聽點擊 $\rightarrow$ 找到那個文字 $\rightarrow$ 修改它的內容 $\rightarrow$ 改變顏色 $\rightarrow$ 隱藏加載圖標。

當頁面變得複雜時，這種模式會導致 **「狀態同步噩夢」** $\rightarrow$ 你改了 A 處，結果 B 處沒更新，C 處突然崩潰。

為了解決這個問題，現代框架引入了 **「聲明式 (Declarative)」** 思考模式 $\rightarrow$ 告訴瀏覽器「我要什麼結果」。
**範例**：`如果 loading 是 true，就顯示轉圈圈；否則顯示數據內容。` $\rightarrow$ 你不再關心如何操作 DOM，框架會幫你同步。

---

## 1. 核心概念：虛擬 DOM 與 響應式 (Reactivity)

為了實現聲明式 UI，框架引入了兩大黑科技：

### A. 虛擬 DOM (Virtual DOM) $\rightarrow$ 減少昂貴的 DOM 操作
瀏覽器操作 DOM 非常慢。框架會在記憶體中建立一個輕量級的 **「虛擬副本」** $\rightarrow$ 當數據改變時，先在副本中計算差異 (Diffing) $\rightarrow$ 只將變動的部分更新到真實 DOM 上 $\rightarrow$ 極大提升性能。

### B. 響應式系統 (Reactivity) $\rightarrow$ 數據驅動視覺
框架會監控你的數據變數 $\rightarrow$ 一旦變數改變 $\rightarrow$ 觸發相關的 UI 組件自動重新渲染。

---

## 2. 視覺化對比：開發者的心智模型

**🚀 實作對比：更新一個計數器**
- **❌ 指令式 (Vanilla JS)**：
  `findElement('#count')` $\rightarrow$ `getCount()` $\rightarrow$ `count++` $\rightarrow$ `setElement('#count', count)`。
- **✅ 聲明式 (Framework)**：
  `count++` $\rightarrow$ **(框架自動更新畫面)**。

**💡 核心價值**：框架將開發者從底層的 DOM 操作中解放出來，讓你能專注於 **「業務邏輯」** 而非 **「DOM 搬運」**。

---

## 3. 如何選擇框架？ (Decision Matrix)

沒有完美的框架，只有最適合場景的選擇：

| 框架 | 特色 | 適用場景 | 學習曲線 |
| :--- | :--- | :--- | :--- |
| **React** | 組件化-生態最強-靈活 | 大型複雜應用-企業級專案 | 中等 |
| **Vue** | 易上手-文檔極佳-漸進式 | 中小型專案-快速原型開發 | 低 |
| **Svelte** | 零 Runtime-編譯時處理-極速 | 極致性能-輕量級網頁 | 中等 |

---

## 🛠️ 框架思考挑戰

1. **對比實作** $\rightarrow$ 用純 JS 實作一個「點擊按鈕文字變色」的功能 $\rightarrow$ 記錄下你寫了多少行代碼。
2. **邏輯轉換** $\rightarrow$ 嘗試將上述功能用「聲明式」的邏輯描述出來 $\rightarrow$ `狀態 (Color) $\rightarrow$ 視覺 (Text Color)`。
3. **分析對比** $\rightarrow$ 在 F12 Network Tab 觀察一個使用框架的網站 $\rightarrow$ 觀察其初始 HTML 是否幾乎為空 (Client-side Rendering) $\rightarrow$ 思考這對 SEO 的影響。

---
<p align="center">
<a href="../08-TypeScript-Era/03-ts-config.md">第3 ts config ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/framework/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-state-management.md">02-state-management ➡️</a>
</p>
