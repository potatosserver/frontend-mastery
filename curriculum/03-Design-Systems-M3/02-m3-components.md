# 02. M3 組件實作 (M3 Components Practical)

在掌握了顏色系統之後，我們不能只是讓網頁「有顏色」，而要讓它「像個產品」。在 M3 中，這意味著我們不再隨意地畫個方塊，而是使用 **標準化組件 (Standardized Components)**。

---

## 📜 為什麼要使用標準組件？

如果你在每個頁面都自己定義按鈕的圓角、高度和陰影 $\rightarrow$ 當設計師要求將所有圓角從 `8px` 改成 `12px` 時，你得在 50 個檔案中手動修改 $\rightarrow$ 這是開發者的噩夢。

**M3 的核心邏輯是：將 UI 拆解為「原子級」的組件。** 只要定義好一套組件規範，你只需要在 HTML 中調用類名，就能確保全站視覺高度一致。

---

## 1. 核心組件：按鈕 (Buttons)

M3 的按鈕不只是「一個可以點擊的方塊」，它根據 **重要程度** 分為不同等級。

**🚀 視覺化對比：**
- **Elevated Button (提升按鈕)**：有輕微陰影 $\rightarrow$ 用於次要操作。
- **Filled Button (填充按鈕)**：高對比顏色 $\rightarrow$ 用於頁面中最核心的 **CTA (Call to Action)**。
- **Outlined Button (輪廓按鈕)**：僅有邊框 $\rightarrow$ 用於低優先級操作（如「取消」）。

**⚡️ 專業實作：**
```css
/* 定義 M3 填充按鈕 */
.btn-filled {
    background-color: var(--md-sys-color-primary);
    color: var(--md-sys-color-on-primary);
    border-radius: 100px; /* M3 標誌性的全圓角 */
    padding: 10px 24px;
    border: none;
    font-weight: 500;
    transition: box-shadow 0.2s ease;
}

.btn-filled:hover {
    box-shadow: 0 2px 8px rgba(0,0,0,0.2);
}
```

---

## 2. 核心組件：卡片 (Cards)

M3 的卡片不再使用沉重的陰影，而是透過 **「表面色 (Surface Color)」** 和 **「微小圓角」** 來區分層級。

**🚀 實作場景：打造一個作品集卡片**
```html
<!-- HTML 結構 -->
<div class="m3-card">
    <div class="card-content">
        <h3 class="card-title">專業個人品牌網站</h3>
        <p class="card-desc">使用 M3 設計系統打造的極簡作品集。</p>
    </div>
    <div class="card-action">
        <button class="btn-outlined">查看詳情</button>
    </div>
</div>
```

```css
/* CSS 樣式 */
.m3-card {
    background-color: var(--md-sys-color-surface-variant);
    border-radius: 12px;
    padding: 16px;
    transition: transform 0.2s ease;
}

.m3-card:hover {
    transform: translateY(-4px);
    background-color: var(--md-sys-color-surface);
}
```

---

## 3. 核心組件：文字欄 (Text Fields)

M3 的文字欄強調 **「狀態反饋」**。當使用者點擊輸入框時，標籤 (Label) 會縮小並上移 $\rightarrow$ 讓使用者始終知道自己在填什麼。

**💡 實作要點：**
- 不要直接使用 `<input>`，而是用 `<div>` 包裹 `<label>` 與 `<input>`。
- 使用 CSS 的 `:focus-within` 偽類來觸發 Label 的上移動畫。

---

## 🛠️ M3 組件挑戰

請在你的主專案中實作以下內容：

1. **建立按鈕組**：實作一個「填充按鈕」、「輪廓按鈕」與「文字按鈕」，並對比它們在頁面上的視覺權重。
2. **打造作品卡片**：建立一個 `.m3-card` $\rightarrow$ 包含圖片區域、標題、描述 $\rightarrow$ 並加上 `hover` 浮起效果。
3. **設計輸入表單**：實作一個 M3 風格的輸入框 $\rightarrow$ 當點擊輸入時，邊框顏色需變為 `--md-sys-color-primary`。

---
<p align="center">
<a href="01-m3-color-system.md">01-m3-color-system ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/m3/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-material-icons.md">03-material-icons ➡️</a>
</p>
