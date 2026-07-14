# 03. 組件模式 (Component Patterns)

如果你只是在寫 HTML 和 CSS $\rightarrow$ 你是在做「網頁」。如果你在設計一個可重複使用的、可擴展的組件庫 $\rightarrow$ 你是在做 **「軟體工程」**。

**組件化 (Componentization)** 的核心目標是：**高內聚，低耦合 (High Cohesion, Low Coupling)**。

---

## 📜 起源：從「頁面」到「組件」的思維轉換

早期的網頁開發是以「頁面」為單位的 $\rightarrow$ `about.html`, `contact.html`。
現代開發是以 **「組件 (Component)」** 為單位的 $\rightarrow$ `Button.jsx`, `Navbar.vue`, `UserCard.tsx`。

**為什麼要這麼做？**
1. **可重複使用** $\rightarrow$ 寫一次 `Button` $\rightarrow$ 全站 100 個頁面共用。
2. **易於測試** $\rightarrow$ 只要 `Button` 單獨測試通過 $\rightarrow$ 不論放在哪裡都能正常工作。
3. **分工協作** $\rightarrow$ A 同事負責 `Navbar` $\rightarrow$ B 同事負責 `Footer` $\rightarrow$ 互不干擾。

---

## 1. 核心模式：容器組件 vs 表現組件 (Container vs Presentational)

這是專業前端最經典的設計模式之一。

### A. 表現組件 (Presentational Components)
- **目標**：只負責 **「怎麼顯示 (How it looks)」**。
- **特點**：沒有業務邏輯 $\rightarrow$ 數據通過 `props` 傳入 $\rightarrow$ 像一個純函數 $\rightarrow$ 給它 A，它顯示 A。
- **範例**：`CustomButton`, `UserAvatar`。

### B. 容器組件 (Container Components) $\rightarrow$ 「大腦」
- **目標**：負責 **「怎麼運作 (How it works)」**。
- **特點**：處理數據抓取 $\rightarrow$ 處理狀態管理 $\rightarrow$ 處理 API 請求 $\rightarrow$ 然後將數據傳給表現組件。
- **範例**：`ProjectListContainer`, `AuthProvider`。

**🚀 視覺化流程：**
`容器組件 (抓數據) $\rightarrow$ 傳遞數據 $\rightarrow$ 表現組件 (畫畫面)`。

---

## 2. 組件通信的三種境界

- **境界 1 (初學者)**：不斷地用 `props` 往下傳 $\rightarrow$ `Props Drilling` (噩夢)。
- **境界 2 (中階)**：使用事件總線 (Event Bus) $\rightarrow$ 隨便發送消息 $\rightarrow$ 容易導致邏輯混亂 $\rightarrow$ 難以追蹤。
- **境界 3 (專業)**：**狀態提升 (Lifting State Up)** $\rightarrow$ 將狀態移至最近的共同祖先 $\rightarrow$ 或是使用 **全局 Store (Zustand/Pinia)**。

---

## 🛠️ 組件模式挑戰

1. **拆解主專案** $\rightarrow$ 觀察你的作品集網站 $\rightarrow$ 找出可以被抽離成「表現組件」的部分 $\rightarrow$ 例如：`WorkCard`, `SectionHeader`。
2. **實作容器模式** $\rightarrow$ 建立一個 `ProjectList` 容器 $\rightarrow$ 負責 `fetch` 數據 $\rightarrow$ 然後將數據傳給多個 `ProjectCard` 表現組件。
3. **設計通用組件** $\rightarrow$ 建立一個 `CustomInput` $\rightarrow$ 通過 `props` 控制其樣式 (例如 `variant="outline"` 或 `variant="filled"`) $\rightarrow$ 實現一套組件的多種視覺表現。

---
<p align="center">
<a href="02-state-management.md">02-state-management ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/framework/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-routing-strategies.md">04-routing-strategies ➡️</a>
</p>
