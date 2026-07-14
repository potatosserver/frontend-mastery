# 02. 狀態管理 (State Management)

當你的應用程式變得複雜 $\rightarrow$ 你會有一個數據 (例如 `userToken`) 需要在 10 個不同的組件中使用 $\rightarrow$ 如果你使用「屬性傳遞 (Props Drilling)」 $\rightarrow$ 你必須將數據像接力賽一樣，通過中間 5 個不需要該數據的組件傳遞下去 $\rightarrow$ 這會導致代碼變得極其難以維護。

為了解決這個問題，我們需要 **狀態管理 (State Management)** $\rightarrow$ 建立一個 **「全局數據倉庫」**。

---

## 📜 起源：從 Props Drilling 到單一數據源

在簡單的組件結構中，數據流向是單向的 $\rightarrow$ 父 $\rightarrow$ 子。但當層級變深時，數據流就變成了噩夢。

**專業工程師的解決方案 $\rightarrow$ 狀態提升 (Lifting State Up) 與 全局 store。**

---

## 1. 視覺化邏輯：狀態管理的三種層級

根據數據的「生存週期」和「使用範圍」，我們將狀態分為三類：

### A. 本地狀態 (Local State)
- **範圍**：僅在單個組件內部使用。
- **工具**：`useState` (React), `ref` (Vue)。
- **場景**：輸入框的文字、按鈕的 Loading 狀態。

### B. 組件間共享狀態 (Shared State)
- **範圍**：在少數幾個相關組件之間共享。
- **工具**：Context API (React), Provide/Inject (Vue)。
- **場景**：目前選中的作品項目。

### C. 全局狀態 (Global State) $\rightarrow$ 「單一真相源」
- **範圍**：整個應用程式隨處可用。
- **工具**：Redux, Zustand, Pinia, Vuex。
- **場景**：使用者登入資訊、全站主題 (深色/淺色)、購物車清單。

---

## 2. 實作對比：Props Drilling vs Global Store

**🚀 噩夢場景 (Props Drilling)：**
`App $\rightarrow$ Layout $\rightarrow$ Header $\rightarrow$ UserProfile $\rightarrow$ UserAvatar` $\rightarrow$ **傳遞 5 層** $\rightarrow$ 只要其中一層改名，整個鏈條崩潰。

**✅ 專業方案 (Global Store)：**
`App $\rightarrow$ Store` $\rightarrow$ `UserAvatar` 直接從 Store 拿數據 $\rightarrow$ **跳過中間所有層級**。

---

## 3. 狀態管理的金科玉律 (Golden Rules)

1. **不要過度使用全局狀態** $\rightarrow$ 如果只有一個組件用，請保持在本地。過多的全局狀態會導致不必要的全頁面重新渲染 $\rightarrow$ 降低性能。
2. **單向數據流** $\rightarrow$ 數據應該從 `Store $\rightarrow$ 組件`。如果要修改數據 $\rightarrow$ 必須發送一個 `Action` $\rightarrow$ 讓 `Reducer/Store` 修改 $\rightarrow$ 再通知組件。

---

## 🛠️ 狀態管理挑戰

1. **分析現有專案** $\rightarrow$ 在你的作品集中，找出哪些數據是「本地」的 $\rightarrow$ 哪些應該提升到「全局」。
2. **設計狀態樹** $\rightarrow$ 繪製你的應用程式狀態圖 $\rightarrow$ 例如：`{ auth: { user: {}, token: "" }, settings: { theme: "dark" } }`。
3. **實作簡單 Store** $\rightarrow$ 嘗試使用一個簡單的 JS 物件作為 Store $\rightarrow$ 實作一個 `subscribe` 模式 $\rightarrow$ 當 Store 改變時，自動更新頁面上的兩個不同組件。

---
<p align="center">
<a href="01-framework-philosophy.md">01-framework-philosophy ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/framework/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-component-patterns.md">03-component-patterns ➡️</a>
</p>
