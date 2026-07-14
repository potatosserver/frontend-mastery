# 04. Web Workers (多執行緒並行處理)

在之前的章節中，我們學到了 JS 是 **單執行緒 (Single-threaded)** 的 $\rightarrow$ 只要有一個耗時的計算，整個網頁就會直接卡死 $\rightarrow$ 使用者無法點擊任何按鈕。

為了解決這個問題，瀏覽器提供了 **Web Workers** $\rightarrow$ 讓 JS 能夠在背景開啟 **「副線程」** 執行繁重任務。

---

## 📜 起源：從「單核」到「多核」的時代

早期的電腦只有一個 CPU 核心，所以單執行緒沒問題。但現代設備（甚至是手機）都有 4 個甚至 8 個核心。如果 JS 永遠只用一個核 $\rightarrow$ 就是在浪費 80% 的運算能力。

**Web Worker** 讓你可以將「計算密集型」的任務 (例如：大量數據處理、圖像分析、複雜數學運算) 移出主執行緒 $\rightarrow$ 確保 UI 永遠保持 60fps 的流暢度。

---

## 1. 視覺化對比：主線程 vs Worker 線程

**🚀 噩夢場景：在主線程計算 1 億次循環**
- **結果**：頁面直接凍結 $\rightarrow$ 按鈕不能點 $\rightarrow$ 動畫停止 $\rightarrow$ 瀏覽器提示「頁面未回應」。

**✅ 專業方案：使用 Worker**
- **主線程 (Main Thread)**：負責 UI 渲染 $\rightarrow$ 接收使用者輸入 $\rightarrow$ 發送指令給 Worker。
- **Worker 線程**：在背景默默計算 $\rightarrow$ 完成後將結果 `postMessage` 回傳給主線程。

---

## 2. 實作：建立你的第一個 Worker

由於 Worker 必須在獨立的檔案中運行，實作流程如下：

**步驟 A：建立 `worker.js` (副線程)**
```javascript
// 監聽來自主線程的消息
self.onmessage = function(e) {
    console.log("Worker 開始計算...");
    let result = 0;
    for (let i = 0; i < 1000000000; i++) { result += i; } // 模擬耗時任務
    self.postMessage(result); // 回傳結果
};
```

**步驟 B：在 `main.js` 中呼叫 (主線程)**
```javascript
const myWorker = new Worker('worker.js');

myWorker.postMessage('start'); // 發送指令

myWorker.onmessage = function(e) {
    console.log("計算完成，結果是: " + e.data);
};
```

---

## 🛠️ Worker 實作挑戰

1. **打造「背景計算器」** $\rightarrow$ 建立一個頁面 $\rightarrow$ 提供一個按鈕「執行繁重計算」 $\rightarrow$ 使用 Worker 執行 $\rightarrow$ 驗證在計算過程中，頁面上的 CSS 動畫依然流暢。
2. **實作「大數據過濾器」** $\rightarrow$ 準備一個 1 萬筆數據的陣列 $\rightarrow$ 在 Worker 中進行複雜的篩選 $\rightarrow$ 將結果回傳至頁面顯示。
3. **錯誤處理** $\rightarrow$ 在 Worker 中故意製造一個錯誤 $\rightarrow$ 使用 `worker.onerror` 在主頁面顯示錯誤訊息。

---
<p align="center">
<a href="03-web-storage-deep.md">03-web-storage-deep ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/browser/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="05-pwa-mastery.md">05-pwa-mastery ➡️</a>
</p>
