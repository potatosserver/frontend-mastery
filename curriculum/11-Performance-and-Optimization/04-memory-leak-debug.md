# 04. 記憶體洩漏調試 (Memory Leak Debug)

如果你發現你的網頁跑了 10 分鐘後 $\rightarrow$ 瀏覽器開始變得緩慢 $\rightarrow$ 最終直接崩潰 $\rightarrow$ 你遇到的是前端開發中最隱蔽的 Bug：**記憶體洩漏 (Memory Leak)**。

---

## 📜 起源：垃圾回收 (Garbage Collection) 的盲點

JS 擁有自動的 **垃圾回收 (GC)** 機制 $\rightarrow$ 當一個變數不再被任何地方引用時 $\rightarrow$ GC 就會把它回收。

但問題在於：如果你的代碼在不經意間創造了 **「不可到達但仍被引用」** 的對象 $\rightarrow$ GC 會認為這個對象「還有用」 $\rightarrow$ 拒絕回收 $\rightarrow$ 記憶體被漸漸填滿。

---

## 1. 三大洩漏元兇 (The Big Three)

專業工程師在審查代碼時，會優先檢查以下三個地方：

### A. 未清除的定時器 (Timers)
- **場景**：在組件中設定了 `setInterval` $\rightarrow$ 組件被銷毀了 $\rightarrow$ 但定時器還在後台運行 $\rightarrow$ 且持有對組件的引用。
- **解決方案**：在 `onUnmount` 時務必執行 `clearInterval()`。

### B. 遺忘的事件監聽器 (Event Listeners)
- **場景**：對 `window` 或 `document` 綁定了 `scroll` 事件 $\rightarrow$ 組件銷毀後 $\rightarrow$ 監聽器依然存在 $\rightarrow$ 導致記憶體不斷累加。
- **解決方案**：在銷毀時執行 `removeEventListener()`。

### C. 閉包 (Closures) 的副作用
- **場景**：一個內層函數引用了巨大的外層變數 $\rightarrow$ 即使外層函數已執行完畢 $\rightarrow$ 只要內層函數還在 (例如被存為全域變數) $\rightarrow$ 整個大變數都無法被回收。

---

## 2. 實作：使用 Memory Tab 獵殺洩漏

不要猜測哪裡洩漏 $\rightarrow$ 使用 Chrome DevTools 的 **Memory Tab**。

**🚀 診斷路徑：**
1. **建立 Heap Snapshot (堆快照)** $\rightarrow$ 記錄當前記憶體狀態 (A)。
2. **執行操作** $\rightarrow$ 進入頁面 $\rightarrow$ 離開頁面 $\rightarrow$ 重複 10 次。
3. **再次建立快照 (B)** $\rightarrow$ 對比 A 與 B。
4. **分析 Comparison** $\rightarrow$ 如果發現某個對象的數量從 1 變成了 10 $\rightarrow$ 而且沒有被回收 $\rightarrow$ 恭喜你，找到了洩漏點。

---

## 🛠️ 記憶體調試挑戰

1. **製造洩漏** $\rightarrow$ 寫一個簡單的頁面 $\rightarrow$ 建立一個 `setInterval` 但不清除 $\rightarrow$ 觀察 Memory Tab 中的 `JS Heap` 曲線是否持續上升。
2. **實作修復** $\rightarrow$ 加入清除邏輯 $\rightarrow$ 驗證記憶體在組件銷毀後是否回到初始水平。
3. **分析第三方庫** $\rightarrow$ 使用 `Heap Snapshot` 分析一個重量級第三方庫 $\rightarrow$ 檢查它是否在卸載後留下了殘餘的 `Detached DOM nodes` (脫離文檔的 DOM 節點)。

---
<p align="center">
<a href="03-bundle-optimization.md">03-bundle-optimization ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/perf/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="https://github.com/your-profile/frontend-ultimate-mastery">完結 ➡️</a>
</p>
