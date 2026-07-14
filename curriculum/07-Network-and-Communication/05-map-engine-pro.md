# 05. 地圖引擎專業實作 (Map Engine Pro)

在前面的模組中，我們學會了獲取地理位置 (Geolocation) $\rightarrow$ 但座標 (緯度, 經度) 對使用者來說只是兩個數字。要將其轉化為**「可交互的視覺地圖」**，我們需要使用 **地圖引擎 (Map Engine)**。

---

## 📜 起源：從圖片地圖到向量地圖

早期的地圖是 **「圖塊地圖 (Raster Tiles)」** $\rightarrow$ 把地球切成無數個小圖片 $\rightarrow$ 縮放時會模糊且緩慢。
現代地圖（如 Google Maps, MapLibre, Mapbox）使用 **「向量地圖 (Vector Tiles)」** $\rightarrow$ 伺服器只發送座標與線條 $\rightarrow$ 由客戶端的 GPU 實時繪製 $\rightarrow$ 縮放絲滑，且可動態修改顏色。

---

## 1. 核心概念：圖層 (Layers) 與 數據源 (Sources)

專業地圖引擎的邏輯像是在畫畫 $\rightarrow$ **一層疊一層**。

- **Source (數據源)** $\rightarrow$ 告訴引擎「數據在哪裡」 (例如：一個包含 100 個作品地點的 JSON 檔案)。
- **Layer (圖層)** $\rightarrow$ 告訴引擎「怎麼畫這些數據」 (例如：用-藍色圓點-來畫地點，用-紅色線條-來畫路線)。

**🚀 視覺化邏輯：**
`底圖 (Base Map)` $\rightarrow$ `道路圖層` $\rightarrow$ `標記圖層 (Markers)` $\rightarrow$ `覆蓋物 (Overlays)`。

---

## 2. 實作：在作品集中整合地圖

**🚀 實作場景：打造「全球作品分佈圖」**
1. **初始化地圖** $\rightarrow$ 設定中心點 (Center) 與 縮放級別 (Zoom)。
2. **添加數據源** $\rightarrow$ 使用 GeoJSON 格式定義作品地點。
3. **添加標記 (Markers)** $\rightarrow$ 為每個作品創建一個可點擊的圓點 $\rightarrow$ 點擊後彈出資訊視窗 (Popup)。

**⚡️ 專業建議：性能優化**
如果你有 10,000 個標記 $\rightarrow$ 不要直接創建 10,000 個 DOM 元素 $\rightarrow$ 必須使用 **標記聚合 (Marker Clustering)** $\rightarrow$ 將靠近的點合並成一個數字圓圈 $\rightarrow$ 縮放後再展開。

---

## 🛠️ 地圖引擎挑戰

1. **建立互動地圖** $\rightarrow$ 使用 MapLibre 或 Leaflet $\rightarrow$ 在頁面上顯示一個全螢幕地圖 $\rightarrow$ 成功標記出 3 個你最自豪的作品地點。
2. **實作自定義 Marker** $\rightarrow$ 不要使用預設的藍色水滴 $\rightarrow$ 使用你自己的 PNG 圖標 $\rightarrow$ 實現「懸停時放大」的視覺效果。
3. **實現座標同步** $\rightarrow$ 結合 `07-Browser-Capabilities` 的地理位置 API $\rightarrow$ 在地圖上實時顯示使用者當前位置 $\rightarrow$ 並計算出距離最近的作品點之距離。

---
<p align="center">
<a href="04-realtime-comm.md">04-realtime-comm ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/net/05-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../08-TypeScript-Era/01-ts-intro.md">01-ts-intro ➡️</a>
</p>
