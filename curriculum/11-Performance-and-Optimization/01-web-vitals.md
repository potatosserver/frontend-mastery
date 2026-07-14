# 01. Core Web Vitals (核心網頁指標)

如果你只覺得網頁「感覺很慢」 $\rightarrow$ 那是主觀的感受。在專業工程領域，我們使用 **Core Web Vitals (CWV)** $\rightarrow$ 將「速度」量化為可以測量的數字。

---

## 📜 起源：Google 的「速度即金錢」理論

Google 發現一個驚人的事實 $\rightarrow$ 當頁面加載時間增加 1 秒 $\rightarrow$ 電商網站的轉單率會下降 7% $\rightarrow$ 對於像 Amazon 這樣的巨頭，這意味著每年損失數十億美元。

因此，Google 推出了 **Core Web Vitals** $\rightarrow$ 將其納入搜尋排名 (SEO) 的評分標準 $\rightarrow$ 強迫全球開發者關注 **「真實使用者的感知速度」**。

---

## 1. 視覺化解析：三大核心指標

專業工程師不再關注 `onload` 總時間，而是關注這三個關鍵維度：

### A. LCP (Largest Contentful Paint) $\rightarrow$ 「主內容出現時間」
- **定義**：頁面中最大那個元素 (通常是橫幅圖或標題) 渲染完成的時間。
- **痛點**：如果 LCP 太慢 $\rightarrow$ 使用者會覺得「頁面還沒開起來」。
- **優化方案**：優先加載主圖 $\rightarrow$ 使用 WebP 格式 $\rightarrow$ 設置 `fetchpriority="high"`。

### B. FID (First Input Delay) $\rightarrow$ 「首次輸入延遲」
- **定義**：使用者第一次點擊按鈕後 $\rightarrow$ 瀏覽器真正做出反應的時間。
- **痛點**：如果你在主線程跑一個巨型 JS 迴圈 $\rightarrow$ 使用者點擊按鈕沒反應 $\rightarrow$ 會感覺頁面「死掉了」。
- **優化方案**：減少主線程 JS 阻塞 $\rightarrow$ 使用 Web Workers $\rightarrow$ 拆分長任務 (Long Tasks)。

### C. CLS (Cumulative Layout Shift) $\rightarrow$ 「累計佈局偏移」
- **定義**：頁面在加載過程中，元素是否會突然「跳動」。
- **痛點**：你正準備點擊「取消」 $\rightarrow$ 突然上方加載了一張廣告 $\rightarrow$ 內容下移 $\rightarrow$ 你點到了「確定」 $\rightarrow$ **這導致極其糟糕的使用者體驗。**
- **優化方案**：為所有圖片和廣告預留固定尺寸 (Aspect Ratio Box)。

---

## 2. 實作：診斷你的作品集性能

請打開 F12 $\rightarrow$ **Lighthouse Tab** $\rightarrow$ 執行一次分析 $\rightarrow$ 觀察你的 LCP, FID, CLS 分數。

**🚀 診斷路徑：**
1. **分析 LCP** $\rightarrow$ 查看 Lighthouse 指出的「最大的內容元素」是什麼 $\rightarrow$ 嘗試將其圖片壓縮 $\rightarrow$ 觀察分數提升。
2. **捕捉 CLS** $\rightarrow$ 在 Performance Tab 中尋找紅色標記的 `Layout Shift` $\rightarrow$ 找出是哪個元素導致了跳動 $\rightarrow$ 為其設置固定寬高。
3. **量化 FID** $\rightarrow$ 使用 Chrome User Experience Report (CrUX) $\rightarrow$ 查看真實使用者的交互延遲數據。

---
<p align="center">
<a href="../10-Engineering-and-QA/04-git-and-ci-cd.md">第4 git and ci cd ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/perf/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-rendering-patterns.md">02-rendering-patterns ➡️</a>
</p>
