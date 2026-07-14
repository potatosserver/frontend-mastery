# 01. 進入 TypeScript 時代 (TypeScript Intro)

在進入代碼之前，我們必須先回答一個最根本的問題：**既然已經有 JavaScript (JS) 了，為什麼我們還需要 TypeScript (TS)？**

---

## 📜 起源：TypeScript 是從哪來的？

TypeScript 是由 **微軟 (Microsoft)** 開發的一種語言。

為什麼微軟要花這麼多資源去創造它？因為他們遇到了**「大規模開發的噩夢」**。想像一下，當你開發的專案規模小到只有幾百行時，JS 的靈活性是優勢；但當你開發像 **VS Code** 或 **Office 網頁版** 這樣擁有數十萬行代碼的工業級產品時，JS 的靈活性就變成了災難。

在純 JS 的世界裡，如果你想把一個變數名從 `userName` 改成 `fullName` $\rightarrow$ 你必須在全專案搜索並手動修改 $\rightarrow$ 只要漏掉一個地方，程式就會在運行時崩潰。這種「祈禱代碼能跑起來」的開發模式，在專業工程領域是不可接受的。

**因此，微軟創造了 TS $\rightarrow$ 讓開發者能在「寫代碼時」就發現錯誤，而不是在「使用者發現」後才來修復。**

---

## 🧩 定位：TS 是什麼？ (The Superset Concept)

很多初學者誤以為 TS 是 JS 的替代品，但正確的理解是：**TS 是 JS 的「超集 (Superset)」**。

- **公式**：$\text{TypeScript} = \text{JavaScript} + \text{Type System (類型系統)}$
- **關係**：所有合法的 JS 代碼，全部都是合法的 TS 代碼。
- **本質**：TS 就像是在 JS 之上加了一層**「智能監控殼」**。它不改變 JS 的運行邏輯，但它在開發階段強迫你定義數據的「形狀」 $\rightarrow$ 確保數據在傳遞過程中不會出錯。

---

## 1. JS 的隱形地雷：為什麼我們需要 TS？

JS 是一種「動態類型」語言。這意味著它非常隨和 $\rightarrow$ 隨和到讓你可以在同一個變數裡先放數字，再放字串，而它完全不抱怨。

**🚀 噩夢場景：**
想像你寫了一個計算總價的函數：
```javascript
function calculateTotal(price, tax) {
    return price + tax;
}

// 正常情況
console.log(calculateTotal(100, 10)); // 110 (正確)

// 災難情況：API 回傳的數據變成了字串
console.log(calculateTotal("100", 10)); // "10010" (崩潰！)
```
在 JS 中，這段代碼**不會報錯**，它會安靜地跑完，然後給出一個錯誤的結果。直到你的使用者抱怨「我的帳單算錯了」時，你才發現 Bug。

**這就是 JS 的痛苦之處：錯誤發生在「執行時 (Runtime)」。**

---

## 2. TS 的救贖：在出錯前攔截錯誤

TypeScript 的核心價值在於 **「靜態分析」**。它在你的代碼還沒運行之前，就幫你檢查一遍邏輯。

**同樣的場景，在 TS 中會變成這樣：**
```typescript
function calculateTotal(price: number, tax: number) {
    return price + tax;
}

// 當你嘗試傳入字串時...
calculateTotal("100", 10); 
// ❌ 編輯器立刻在 "100" 下方畫紅線！
// 錯誤訊息：Argument of type 'string' is not assignable to parameter of type 'number'.
```

**💡 這就是 TS 的魔力：**
它把 Bug 的發現時間，從 **「使用者發現 $\rightarrow$ 報錯 $\rightarrow$ 修復」** 提前到了 **「工程師打字 $\rightarrow$ 看到紅線 $\rightarrow$ 修復」**。

---

## 3. 揭開真相：TS 其實不能直接運行

很多初學者會問：「既然 TS 這麼好，為什麼瀏覽器不直接支援 TS？」

**答案是：瀏覽器根本看不懂 TS。**

瀏覽器（Chrome, Safari, Firefox）只認識 HTML, CSS 和 JavaScript。因此, TS 必須經過一個 **「翻譯過程」 $\rightarrow$ 編譯 (Compilation)**。

**🚀 TS 運作流程圖：**
`你的 TS 代碼 (.ts)` $\rightarrow$ `TS 編譯器 (tsc)` $\rightarrow$ `產出的 JS 代碼 (.js)` $\rightarrow$ `瀏覽器執行`

**所以，TS 的定位是：**
- **開發時**：它是你的「智能助手」，提供精確的類型檢查和強大的自動補完 (IntelliSense)。
- **交付時**：它會被翻譯成純 JS，確保在所有環境中都能運行。

---

## 4. 為什麼這對開發者來說是好事？ (DX: Developer Experience)

學習 TS 雖然增加了一點點寫代碼的成本，但它極大地提升了 **開發體驗 (DX)**：

1. **再也不用猜變數是什麼**：看到 `user: UserProfile`，你就知道裡面有 `name`, `email` 等屬性，不用切換檔案回去確認。
2. **無痛重構**：如果你想把 `userName` 改名為 `fullName` $\rightarrow$ 只需一次重命名，TS 會幫你把全專案所有用到這個變數的地方全部修正 $\rightarrow$ 且保證沒有漏掉任何一個。
3. **自備文檔**：類型定義本身就是最好的文檔。新加入的同事只要看類型，就知道這個函數需要傳入什麼，回傳什麼。

---

## 🛠️ 第一步實作：設定你的 TS 環境

TS 不能像 HTML 那樣直接打開就跑，你需要安裝編譯器。

1. **安裝 Node.js** (如果還沒安裝)。
2. **安裝 TypeScript 編譯器**：
```bash
npm install -g typescript
```
3. **嘗試編譯**：
   - 建立 `hello.ts` $\rightarrow$ 寫入 `let msg: string = "Hello TS"; console.log(msg);`
   - 執行 `tsc hello.ts` $\rightarrow$ 你會發現資料夾裡多了一個 `hello.js`。
   - 運行 `node hello.js` $\rightarrow$ 看到結果。

---
<p align="center">
<a href="../07-Network-and-Communication/05-map-engine-pro.md">第5 map engine pro ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/ts/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-ts-types.md">02-ts-types ➡️</a>
</p>
