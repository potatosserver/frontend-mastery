# 05. PWA 掌握指南 (PWA Mastery)

如果你的網頁只能在「有網路」時才能開啟 $\rightarrow$ 那它只是一個「文件」。如果你希望你的網頁能像 App 一樣 **「安裝到手機」** 且 **「離線也能運行」** $\rightarrow$ 你需要 **PWA (Progressive Web App)**。

---

## 📜 起源：打破「瀏覽器」的圍牆

早期的移動端體驗很糟糕 $\rightarrow$ 想要 App 必須去 App Store 下載 $\rightarrow$ 流程冗長 $\rightarrow$ 更新緩慢。
Google 推出了 PWA 規範 $\rightarrow$ 讓開發者可以用純 Web 技術，打造出具有 **原生 App 體驗** 的網頁。

**PWA 的三大支柱：**
1. **HTTPS (安全)**：必須使用加密傳輸。
2. **Web App Manifest (身份證)**：告訴手機這個網頁的名字、圖標、啟動頁面是什麼。
3. **Service Worker (核心引擎)**：一個在背景運行的代理伺服器 $\rightarrow$ 負責快取資源 $\rightarrow$ 實現離線訪問。

---

## 1. 視覺化目標：打造「離線可用」的作品集

想像使用者在地鐵（沒網路）時，依然能打開你的作品集 $\rightarrow$ 看到之前的快照 $\rightarrow$ 感覺像是在使用安裝好的 App。

**🚀 實作路徑：**
1. **建立 `manifest.json`** $\rightarrow$ 定義 `short_name`, `start_url`, `display: standalone`。
2. **註冊 Service Worker** $\rightarrow$ 在 `main.js` 中檢查 `navigator.serviceWorker`。
3. **實作快取策略 (Caching Strategy)** $\rightarrow$ 在 SW 中使用 `Cache API` $\rightarrow$ 將 HTML/CSS/JS 預先存入快取。

**⚡️ 專業代碼實作 (Service Worker 簡化版)：**
```javascript
self.addEventListener('install', (event) => {
    event.waitUntil(
        caches.open('v1').then((cache) => {
            return cache.addAll(['/', '/style.css', '/main.js']);
        })
    );
});

self.addEventListener('fetch', (event) => {
    event.respondWith(
        caches.match(event.request).then((response) => {
            return response || fetch(event.request);
        })
    );
});
```

---

## 2. 實作挑戰：將網站 PWA 化

1. **建立 Manifest** $\rightarrow$ 完成 `manifest.json` 並在 HTML 中引入 $\rightarrow$ 嘗試在 Chrome 中點擊「安裝到桌面」。
2. **實現基礎離線頁面** $\rightarrow$ 當網路完全斷開時 $\rightarrow$ 顯示一個自定義的 `offline.html` 頁面。
3. **分析快取效能** $\rightarrow$ 在 F12 的 **Application Tab** $\rightarrow$ 檢查 `Cache Storage` 中是否成功存入了所有資源。

---
<p align="center">
<a href="04-web-workers.md">04-web-workers ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/browser/05-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../07-Network-and-Communication/01-http-deep-dive.md">01-http-deep-dive ➡️</a>
</p>
