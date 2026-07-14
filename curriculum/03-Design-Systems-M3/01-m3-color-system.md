# 01. M3 顏色系統 (M3 Color System)

在學習具體的組件之前，我們必須先理解一個核心概念：**為什麼 Google 要花這麼多時間定義一套「顏色系統」，而不是直接讓我們選顏色？**

---

## 📜 起源：什麼是 Material Design 3 (M3)？

**Material Design** 是由 **Google** 創造的一套設計語言 (Design Language)。它的目的不是為了「好看」，而是為了**「標準化」**。

想像一下，如果一個公司有 100 個工程師，每個人對「主色調」的理解都不同 $\rightarrow$ 有的人用 `#3f51b5`，有的人用 `#3b5998` $\rightarrow$ 最終產品會像一塊補丁布。Google 創造 M3 是為了讓全世界的開發者都能用同一套「視覺語言」來溝通。

**從 M1 $\rightarrow$ M2 $\rightarrow$ M3 的演進：**
- **M1 (擬物化)**：強調陰影、層級與深度 (像是現實中的紙張堆疊)。
- **M2 (扁平化)**：追求簡潔、明快，確立了鮮明的色彩對比。
- **M3 (Material You)**：這是目前的最新版本。核心概念是 **「個性化 (Personalization)」**。它不再強迫所有使用者使用同一種顏色，而是能根據使用者的壁紙自動提取色調 $\rightarrow$ 讓 UI 具有適應性。

---

## 1. 顏色系統的核心：色調調色盤 (Tonal Palettes)

在 M3 中，我們不再談論單一的「顏色」，而是談論 **「色調 (Tone)」**。

一個顏色由 **「色相 (Hue)」** 和 **「亮度 (Luminance)」** 組成。M3 定義了一套從 0 (黑) 到 100 (白) 的亮度階梯。

**🚀 視覺化邏輯：**
- **Primary (主色)**：品牌的核心色，用於最關鍵的按鈕和狀態。
- **Secondary (輔色)**：用於較不顯眼的 UI 元素，增加層次感。
- **Tertiary (三級色)**：用於對比或強調某些特殊功能。
- **Surface (表面色)**：背景色，決定了頁面的整體基調。

---

## 2. 實作：如何將 M3 顏色應用到 CSS 中？

專業工程師絕不會在 CSS 中直接寫 `color: #FF0000;`。我們會使用 **CSS 變數 (Custom Properties)** 來建立一套主題系統。

**🚀 實作對比：**
- **❌ 初學者寫法**：
```css
.btn-primary {
    background-color: #6750A4;
    color: white;
}
```
- **✅ 專業 M3 寫法**：
```css
:root {
    --md-sys-color-primary: #6750A4;
    --md-sys-color-on-primary: #FFFFFF;
}

.btn-primary {
    background-color: var(--md-sys-color-primary);
    color: var(--md-sys-color-on-primary);
}
```
**💡 為什麼要這樣做？**
如果你以後想把全站的紫色改成藍色 $\rightarrow$ 你只需要修改 `:root` 裡的一行變數 $\rightarrow$ 全站所有按鈕會瞬間同步更新。這就是 **「設計系統 (Design System)」** 的強大之處。

---

## 3. 實作挑戰：建立你的 M3 基礎配色方案

請在你的 `style.css` 中嘗試以下步驟：

1. **定義變數**：建立 `:root`，定義 `--md-sys-color-primary` (主色) 與 `--md-sys-color-surface` (背景色)。
2. **應用顏色**：建立一個 `.card` 組件 $\rightarrow$ 背景色使用 `--md-sys-color-surface` $\rightarrow$ 邊框色使用 `--md-sys-color-primary`。
3. **測試切換**：嘗試修改 `:root` 中的顏色值 $\rightarrow$ 觀察 `.card` 的視覺變化。

---
<p align="center">
<a href="../02-CSS-Mastery/06-responsive-design.md">第6 responsive design ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/m3/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-m3-components.md">02-m3-components ➡️</a>
</p>
