# 01. DOM 性能與渲染管線 (DOM Performance & Pipeline)

在之前的模組中，我們學會了如何操作 DOM。但如果你在一個有 10,000 個元素的頁面中頻繁修改樣式 $\rightarrow$ 你會發現網頁開始「卡頓」 $\rightarrow$ 即使你的 JS 代碼寫得很高效。

這是因為你觸發了瀏覽器的 **「渲染地獄」**。

---

## 📜 起源：瀏覽器是如何「畫」出網頁的？

瀏覽器將 HTML/CSS 轉化為像素的過程稱為 **關鍵渲染路徑 (Critical Rendering Path)**。

**流程如下：**
`HTML $\rightarrow$ DOM Tree` $\rightarrow$ `CSS $\rightarrow$ CSSOM Tree` $\rightarrow$ `Render Tree` $\rightarrow$ `Layout (排版)` $\rightarrow$ `Paint (繪製)` $\rightarrow$ `Composite (合成)`。

**專業工程師的痛點 $\rightarrow$ 回流 (Reflow) 與 重繪 (Repaint)：**
- **回流 (Reflow)**：當你修改 `width` 或 `height` 時，瀏覽器必須重新計算整個頁面的佈局 $\rightarrow$ **極其耗能**。
- **重繪 (Repaint)**：當你只修改 `color` 或 `background-color` 時，瀏覽器只需重新上色 $\rightarrow$ **較快，但仍有成本**。

---

## 1. 視覺化對比：讓動畫從 15fps 變成 60fps

**🚀 實作對比：如何移動一個元素？**
- **❌ 業餘寫法 (觸發 Reflow)**：使用 `top` 或 `left`。
```css
.box { position: absolute; top: 0; left: 0; transition: top 0.3s; }
.box.move { top: 100px; }
```
- **✅ 專業寫法 (觸發 GPU 合成)**：使用 `transform: translate`。
```css
.box { position: absolute; transition: transform 0.3s; }
.box.move { transform: translateY(100px); }
```
**💡 為什麼？** `transform` 不會觸發 Layout，它直接在瀏覽器的 **合成層 (Composite Layer)** 處理 $\rightarrow$ 速度極快，且完全流暢。

---

## 2. 實作挑戰：診斷你的頁面性能

請在你的主專案中嘗試以下步驟：

1. **觸發卡頓**：寫一個 JS 迴圈 $\rightarrow$ 瞬間修改 100 個元素的 `width` $\rightarrow$ 打開 F12 $\rightarrow$ 在 **Performance Tab** 觀察紫色的 `Layout` 區塊。
2. **性能優化**：將 `width` 修改改為 `transform: scale()` $\rightarrow$ 再次觀察 Performance Tab $\rightarrow$ 確認 Layout 時間大幅減少。
3. **減少 DOM 操作**：嘗試使用 `document.createDocumentFragment()` 一次性插入 100 個元素 $\rightarrow$ 對比直接用 `appendChild` 100 次的耗時。

---
<p align="center">
<a href="../05-The-Art-of-F12-and-API/04-cors-and-proxy.md">第4 cors and proxy ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/browser/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-browser-api-geo.md">02-browser-api-geo ➡️</a>
</p>
