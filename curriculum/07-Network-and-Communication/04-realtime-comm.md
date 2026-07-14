# 04. 實時通訊 (Real-time Communication)

在之前的章節中，所有的通訊都是 **「單向的 (Unary)」** $\rightarrow$ 客戶端問，伺服器答 $\rightarrow$ 答完就斷開。如果你想做一個「聊天室」或「即時通知」 $\rightarrow$ 讓伺服器主動推送數據給客戶端，這就需要 **實時通訊 (Real-time)**。

---

## 📜 起源：從「輪詢」到「全雙工」

早期的實時方案是 **輪詢 (Polling)** $\rightarrow$ 瀏覽器每隔 1 秒問一次：「有新訊息嗎？」 $\rightarrow$ 伺服器回：「沒有」。這導致極大的流量浪費與伺服器壓力。

為了解決這個問題，業界推出了 **WebSocket** $\rightarrow$ 建立一個 **「全雙工 (Full-Duplex)」** 的長連接 $\rightarrow$ 伺服器可以隨時主動推送數據，而不需要客戶端請求。

---

## 1. WebSocket vs HTTP (視覺化對比)

**🚀 HTTP 模式 (像寄信)**：
`客戶端 $\rightarrow$ (信件) $\rightarrow$ 伺服器` $\rightarrow$ `伺服器 $\rightarrow$ (回信) $\rightarrow$ 客戶端` $\rightarrow$ **連接斷開**。

**✅ WebSocket 模式 (像打電話)**：
`客戶端 $\leftrightarrow$ (建立通道) $\leftrightarrow$ 伺服器` $\rightarrow$ **通道保持開啟** $\rightarrow$ 雙方隨時說話。

---

## 2. 實作：建立你的第一個實時通道

WebSocket 的 API 非常簡單，但需要一個支持 WebSocket 的伺服器。

**⚡️ 實作代碼：**
```javascript
// 建立連接
const socket = new WebSocket('wss://echo.websocket.events');

// 監聽開啟
socket.onopen = () => {
    console.log("通道已開啟！");
    socket.send("Hello Server!"); // 發送訊息
};

// 監聽訊息回傳
socket.onmessage = (event) => {
    console.log("收到伺服器推送: " + event.data);
};

// 監聽關閉
socket.onclose = () => {
    console.log("連接已關閉");
};
```

---

## 3. 進階：SSE (Server-Sent Events)

如果你只需要 **「伺服器 $\rightarrow$ 客戶端」** 的單向推送（例如：股票價格更新、ChatGPT 的打字機效果），不需要客戶端回傳數據 $\rightarrow$ **SSE** 是比 WebSocket 更輕量、更穩定的選擇。

- **特點**：基於標準 HTTP $\rightarrow$ 只要伺服器一直不關閉連接 $\rightarrow$ 數據就會像流水一樣源源不斷地湧入。

---

## 🛠️ 實時通訊挑戰

1. **實作簡易聊天室** $\rightarrow$ 使用 WebSocket 連接一個公共 Echo 伺服器 $\rightarrow$ 實作「輸入框 $\rightarrow$ 發送 $\rightarrow$ 在頁面上顯示回傳訊息」的流程。
2. **打造即時通知提醒** $\rightarrow$ 使用 SSE 或 WebSocket $\rightarrow$ 在頁面右上角實作一個「新訊息」的紅色小紅點動畫。
3. **對比效能** $\rightarrow$ 實作一個簡單的輪詢 (setInterval) $\rightarrow$ 對比 WebSocket 的延遲 (Latency) $\rightarrow$ 觀察 F12 Network Tab 中 `WS` 類型的連接狀態。

---
<p align="center">
<a href="03-rest-vs-graphql.md">03-rest-vs-graphql ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/net/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="05-map-engine-pro.md">05-map-engine-pro ➡️</a>
</p>
