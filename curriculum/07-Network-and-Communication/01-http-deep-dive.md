# 01. HTTP 深度剖析 (HTTP Deep Dive)

如果你只會用 `fetch` 抓數據，而不知道數據是如何在網線中傳輸的 $\rightarrow$ 當你遇到 `403 Forbidden` 或 `502 Bad Gateway` 時，你只能盲目地嘗試。

要成為專業前端，你必須理解 **HTTP (超文本傳輸協定)** $\rightarrow$ 它是整個互聯網的「共同語言」。

---

## 📜 起源：為什麼需要 HTTP？

在互聯網早期，不同的電腦之間沒有統一的溝通方式。如果 A 電腦想向 B 電腦要一個檔案，它得知道 B 電腦的特定內部格式。

為了讓全世界的瀏覽器和伺服器能互相對話，W3C 定義了 HTTP $\rightarrow$ 一種基於 **「請求 (Request)」** 與 **「回應 (Response)」** 的簡單協議。

---

## 1. 視覺化請求流程：一次點擊背後發生了什麼？

當你在瀏覽器輸入 `google.com` 並按下 Enter $\rightarrow$ 實際上發生了以下過程：
1. **DNS 解析** $\rightarrow$ 瀏覽器問 DNS 伺服器：「google.com 的 IP 地址是多少？」 $\rightarrow$ 得到 `142.250.xxx.xxx`。
2. **建立 TCP 連接** $\rightarrow$ 瀏覽器與伺服器進行「三次握手」，確保雙方都在線。
3. **發送 HTTP 請求** $\rightarrow$ 瀏覽器發送：`GET /index.html HTTP/1.1`。
4. **伺服器回應** $\rightarrow$ 伺服器回傳：`HTTP/1.1 200 OK` $\rightarrow$ 附帶 HTML 內容。

---

## 2. 專業工程師必須掌握的狀態碼 (Status Codes)

不要只記 `200`。專業開發者會根據狀態碼的第一位數字快速判斷問題所在：

- **1xx (資訊)** $\rightarrow$ 請求已收到，繼續處理。
- **2xx (成功)** $\rightarrow$ `200 OK` (成功), `201 Created` (資源已建立)。
- **3xx (重新定向)** $\rightarrow$ `301 Moved Permanently` (永久搬家 $\rightarrow$ 對 SEO 極其重要)。
- **4xx (客戶端錯誤)** $\rightarrow$ `400 Bad Request` (參數錯), `401 Unauthorized` (沒登入), `403 Forbidden` (沒權限), `404 Not Found` (找不到頁面)。
- **5xx (伺服器錯誤)** $\rightarrow$ `500 Internal Server Error` (後端程式崩潰), `504 Gateway Timeout` (伺服器太久沒回應)。

---

## 3. 實作：分析真實的 HTTP 流量

請打開 F12 $\rightarrow$ **Network Tab** $\rightarrow$ 隨便刷新一個網頁 $\rightarrow$ 觀察以下內容：
1. **Header (標頭)**：查看 `Request Headers` (你發了什麼) 與 `Response Headers` (伺服器回了什麼)。
2. **Payload (負載)**：如果你在提交表單 $\rightarrow$ 觀察 `Payload` 標籤 $\rightarrow$ 檢查數據是否以 `JSON` 或 `FormData` 格式發送。
3. **Timing (時間線)**：觀察 `TTFB (Time to First Byte)` $\rightarrow$ 判斷是網路慢，還是伺服器處理太慢。

---
<p align="center">
<a href="../06-Browser-Capabilities/05-pwa-mastery.md">第5 pwa mastery ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/net/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-security-hardening.md">02-security-hardening ➡️</a>
</p>
