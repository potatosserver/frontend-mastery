# 03. 包體優化深潛 (Bundle Optimization)

如果你發現你的 JS 檔案大小達到了 2MB $\rightarrow$ 使用者在 3G 網路下需要等待 10 秒才能看到頁面 $\rightarrow$ 這就是 **「包體臃腫 (Bundle Bloat)」**。

專業工程師的目標是：**只讓使用者下載「目前頁面真正需要」的代碼。**

---

## 📜 起源：從單一 Bundle 到模塊化拆分

早期的打包工具將所有代碼打成一個 `bundle.js` $\rightarrow$ 只要你修改一個字，使用者就得重新下載整個 2MB 的檔案 $\rightarrow$ 極其低效。

為了解決這個問題，現代打包工具引入了 **「代碼分割 (Code Splitting)」** 與 **「搖樹優化 (Tree Shaking)」**。

---

## 1. 核心技術：如何砍掉多餘的代碼？

### A. Tree Shaking (搖樹優化)
- **原理**：像搖樹一樣，把沒有被使用的「死代碼 (Dead Code)」全部搖掉。
- **關鍵**：必須使用 **ES Modules (`import` / `export`)** $\rightarrow$ 因為它們是靜態的 $\rightarrow$ 打包工具在構建時就能確定哪些函數沒被用到。
- **🚀 實作對比**：
  - `import _ from 'lodash'` $\rightarrow$ 引入整個庫 (臃腫)。
  - `import { debounce } from 'lodash-es'` $\rightarrow$ 只引入單個函數 (精簡)。

### B. Code Splitting (代碼分割) $\rightarrow$ 懶加載 (Lazy Loading)
- **原理**：將大檔案拆分成多個小碎片 $\rightarrow$ 只有當使用者進入特定頁面時 $\rightarrow$ 才下載該頁面的 JS。
- **⚡️ 實作技巧**：使用 `import()` 動態導入。
```javascript
// 只有點擊按鈕時，才下載重量級的圖表庫
button.onclick = async () => {
    const { renderChart } = await import('./charts.js');
    renderChart();
};
```

---

## 2. 視覺化分析：找出誰在佔空間

不要猜測哪個庫最重 $\rightarrow$ 使用 **Bundle Analyzer**。

**🚀 診斷路徑：**
1. 安裝 `rollup-plugin-visualizer` 或 `webpack-bundle-analyzer`。
2. 執行 Build $\rightarrow$ 生成一個 **「矩形樹圖 (Treemap)」**。
3. 觀察圖中最大的矩形 $\rightarrow$ 發現某個庫佔了 500KB $\rightarrow$ 尋找更輕量的替代品 (例如：用 `dayjs` 替換 `moment.js`)。

---

## 🛠️ 包體優化挑戰

1. **實作懶加載** $\rightarrow$ 將你的作品集中的「關於我」或「詳細作品頁」改為動態導入 $\rightarrow$ 觀察 Network Tab $\rightarrow$ 確認在進入頁面前不會下載對應的 JS。
2. **執行搖樹優化** $\rightarrow$ 建立一個具有 10 個函數的工具庫 $\rightarrow$ 在主檔案中只使用 1 個 $\rightarrow$ 檢查打包後的 `.js` 檔案 $\rightarrow$ 確認其他 9 個函數已被剔除。
3. **替換重量級庫** $\rightarrow$ 找出專案中的大體積依賴 $\rightarrow$ 使用 `bundlephobia.com` 尋找更輕量的替代方案 $\rightarrow$ 記錄體積減少的百分比。

---
<p align="center">
<a href="02-rendering-patterns.md">02-rendering-patterns ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/perf/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-memory-leak-debug.md">04-memory-leak-debug ➡️</a>
</p>
