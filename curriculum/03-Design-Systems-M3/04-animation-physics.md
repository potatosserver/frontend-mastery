# 04. 動畫物理學 (Animation Physics)

很多初學者寫動畫時，習慣使用 `transition: all 0.3s linear;` $\rightarrow$ 結果就是動畫看起來像機器人，僵硬且不自然。

**專業前端工程師知道：真正的自然感來自於對「物理世界」的模仿。**

---

## 📜 起源：為什麼是物理動畫？

在現實生活中，沒有任何東西是「勻速運動」的。
- 當你推一個球 $\rightarrow$ 它會從快變慢 (Deceleration)。
- 當你拉一個彈簧 $\rightarrow$ 它會來回震盪 (Spring/Bounce)。

Google M3 的動畫核心在於 **「貝茲曲線 (Bézier Curves)」** 與 **「彈性 (Springs)」**。目標是讓 UI 感覺像是有「重量」和「慣性」的實體。

---

## 1. 擺脫 Linear：掌握 Easing Functions

不要使用 `linear`。請嘗試以下三種專業曲線：

- **Ease-in** $\rightarrow$ 慢起快停 (像汽車起步)。
- **Ease-out** $\rightarrow$ 快起慢停 (像剎車 $\rightarrow$ **最適合用於進入頁面的元素**)。
- **Ease-in-out** $\rightarrow$ 慢起慢停 (像自然的擺動)。

**🚀 實作對比：**
```css
/* ❌ 僵硬的動畫 */
.box { transition: transform 0.3s linear; }

/* ✅ 自然的 M3 動畫 */
.box { transition: transform 0.3s cubic-bezier(0.2, 0, 0, 1); }
```

---

## 2. 核心技巧：微互動 (Micro-interactions)

M3 的精髓在於「微小的反饋」。

**🚀 實作場景：按鈕的「按壓感」**
不要只是改變顏色，要改變 **「縮放比例」**。
```css
.btn-m3 {
    transition: transform 0.1s cubic-bezier(0.4, 0, 0.2, 1);
}

.btn-m3:active {
    transform: scale(0.95); /* 輕微縮小，創造按下實體按鈕的錯覺 */
}
```

---

## 3. 實作挑戰：打造「有靈魂」的 UI

請在你的主專案中實作以下動畫：

1. **側邊欄滑入**：建立一個側邊導航欄 $\rightarrow$ 使用 `cubic-bezier(0.05, 0.7, 0.1, 1.0)` 實現快速進入、緩慢停止的滑入效果。
2. **卡片懸浮**：讓作品卡片在 `hover` 時不僅上升，還要有輕微的陰影擴散 $\rightarrow$ 模擬 z 軸高度的增加。
3. **加載動畫**：實作一個 M3 風格的圓形進度條 $\rightarrow$ 使用 `infinite` 循環 $\rightarrow$ 確保其旋轉曲線是平滑的。

---
<p align="center">
<a href="03-material-icons.md">03-material-icons ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/m3/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../04-JS-Mastery/01-basics-and-variables.md">01-basics-and-variables ➡️</a>
</p>
