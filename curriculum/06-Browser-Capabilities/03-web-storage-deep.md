# 03. 網頁存儲深潛 (Web Storage Deep Dive)

如果你刷新頁面 $\rightarrow$ 所有的 JS 變數全部消失。這對使用者來說是災難 $\rightarrow$ 例如：購物車被清空、登入狀態消失、深色模式切換回淺色。

為了讓網頁擁有 **「記憶力」**，我們需要 **Web Storage**。

---

## 📜 起源：從 Cookie 到 localStorage

早期的網頁依賴 **Cookie** $\rightarrow$ 但 Cookie 空間極小 (4KB) 且每次請求都會發送到伺服器 $\rightarrow$ 嚴重拖慢速度。
W3C 因此推出了 **Web Storage API** $\rightarrow$ 將數據直接儲存在使用者的瀏覽器硬碟中 $\rightarrow$ 速度快、容量大、且不影響網路請求。

---

## 1. 三大存儲方案對比 (Decision Matrix)

專業工程師不會隨便選存儲方式，而是根據 **「數據生命週期」** 來選擇：

| 方案 | 持久度 | 容量 | 特點 | 適用場景 |
| :--- | :--- | :--- | :--- | :--- |
| **SessionStorage** | 關閉分頁即消失 | ~5MB | 僅限當前分頁 | 一次性表單、臨時狀態 |
| **LocalStorage** | 除非手動刪除，否則永久 | ~5MB | 全分頁共享 | **主題設定 (深色/淺色)**、使用者偏好 |
| **IndexedDB** | 永久 | 極大 (GB級) | 異步、支持索引 | 離線緩存、複雜數據集 (如本地資料庫) |

---

## 2. 實作：打造「記憶力」作品集

讓我們讓你的作品集擁有記憶力 $\rightarrow$ 記錄使用者的主題偏好。

**🚀 實作路徑：**
1. **儲存設定** $\rightarrow$ 當使用者點擊深色模式 $\rightarrow$ `localStorage.setItem('theme', 'dark')`。
2. **讀取設定** $\rightarrow$ 頁面載入時 $\rightarrow$ `const theme = localStorage.getItem('theme')`。
3. **同步視覺** $\rightarrow$ 如果 `theme === 'dark'` $\rightarrow$ 給 `body` 加上 `.dark-mode` 類名。

**⚡️ 專業提醒：JSON 序列化**
`localStorage` 只能存 **字串**。如果你想存一個物件 $\rightarrow$ 必須使用 `JSON.stringify` 和 `JSON.parse`。
```javascript
const userPrefs = { theme: 'dark', font: 'Inter' };
localStorage.setItem('prefs', JSON.stringify(userPrefs)); // 儲存
const savedPrefs = JSON.parse(localStorage.getItem('prefs')); // 取回
```

---

## 🛠️ 存儲實作挑戰

1. **實作主題切換記憶** $\rightarrow$ 確保使用者刷新頁面後，之前的深色/淺色選擇依然生效。
2. **打造「最近瀏覽」清單** $\rightarrow$ 監控使用者點擊了哪些作品卡片 $\rightarrow$ 將 ID 存入 `localStorage` 陣列 $\rightarrow$ 在首頁顯示「您最近看過...」。
3. **對比 Session vs Local** $\rightarrow$ 實作一個簡單的計數器 $\rightarrow$ 一個用 `SessionStorage` $\rightarrow$ 一個用 `LocalStorage` $\rightarrow$ 嘗試關閉分頁後觀察誰還記得數字。

---
<p align="center">
<a href="02-browser-api-geo.md">02-browser-api-geo ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/browser/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-web-workers.md">04-web-workers ➡️</a>
</p>
