# 03. Material Icons (視覺符號系統)

在 M3 中，圖標 (Icons) 不是為了裝飾，而是為了**「傳遞功能意義」**。一個好的圖標應該讓使用者在不閱讀文字的情況下，就能立刻知道這個按鈕是做什麼的。

---

## 📜 起源：為什麼不直接用圖片？

早期的網頁使用 `.png` 或 `.jpg` 作為圖標 $\rightarrow$ 缺點是：縮放會模糊、無法用 CSS 改變顏色、增加 HTTP 請求數量導致加載慢。

Google 推出的 **Material Symbols** 是基於 **SVG (可縮放向量圖形)** 的字體系統 $\rightarrow$ 它將圖標視為「文字」。這意味著你可以像修改字體大小一樣修改圖標大小，像修改文字顏色一樣修改圖標顏色。

---

## 1. 視覺語義：圖標的選擇邏輯

在 M3 中，圖標分為三種風格：
- **Outlined (輪廓)**：最輕量 $\rightarrow$ 用於一般狀態。
- **Filled (填充)**：最沉重 $\rightarrow$ 用於「激活」或「選中」狀態。
- **Rounded (圓角)**：最親和 $\rightarrow$ 適用於消費者產品。

**🚀 實作場景：導航欄的狀態切換**
- 當使用者在「首頁」時 $\rightarrow$ 首頁圖標應從 `home_outlined` 變為 `home` (Filled)。

---

## 2. 實作：將 Material Icons 注入網頁

最專業的實作方式是使用 Google 提供的 Web Font。

**⚡️ 實作步驟：**
1. 在 `<head>` 中引入 Google Fonts 的 Symbol 連結。
2. 使用特定的類名 `material-symbols-outlined`。

```html
<!-- 引入 Google Symbols -->
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200" />

<!-- 使用圖標 -->
<button class="btn-icon">
    <span class="material-symbols-outlined">settings</span>
    設定
</button>
```

```css
.btn-icon {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    background: var(--md-sys-color-surface);
    border: 1px solid var(--md-sys-color-outline);
    border-radius: 100px;
    cursor: pointer;
}

.material-symbols-outlined {
    font-size: 20px;
    color: var(--md-sys-color-primary);
}
```

---

## 🛠️ 圖標實作挑戰

1. **建立導航欄**：實作一個底部導航欄 $\rightarrow$ 包含「首頁」、「搜尋」、「設定」三個圖標。
2. **實作狀態切換**：使用 JS 讓點擊後的圖標變色，並將 `font-variation-settings` 中的 `FILL` 從 `0` 改為 `1`。
3. **尺寸適應**：實作一個大型的 Feature 區域 $\rightarrow$ 使用 48px 的圖標 $\rightarrow$ 確保其垂直居中。

---
<p align="center">
<a href="02-m3-components.md">02-m3-components ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/m3/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-animation-physics.md">04-animation-physics ➡️</a>
</p>
