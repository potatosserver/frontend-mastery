# 01. 網頁是什麼？ (What is the Web?)

在學習寫程式之前，你必須先理解你所處的環境。網頁開發的核心其實就是處理 **「數據的傳輸」** 與 **「數據的呈現」**。

## 1. 客戶端與伺服器的協作 (Client-Server Model)

整個網路的運作基於一個簡單的模型：**請求 (Request)** 與 **響應 (Response)**。

- **客戶端 (Client)**：就是你的瀏覽器 (Chrome, Firefox, Safari)。它是「請求者」，負責向伺服器要求資料並將其呈現給使用者。
- **伺服器 (Server)**：一台 24 小時開機、存放網站檔案的強大電腦。它是「提供者」，負責接收請求、處理邏輯（如檢查資料庫），然後把結果傳回給客戶端。

**比喻：** 就像在餐廳點餐。你是客戶端 $\rightarrow$ 服務生是網路 $\rightarrow$ 廚房是伺服器。你點餐 (Request)，廚房做菜，最後服務生把菜端給你 (Response)。

---

## 2. 當你輸入 URL 後發生了什麼？ (The Journey of a Request)

假設你在瀏覽器輸入 `https://www.google.com` 並按下 Enter，在不到 1 秒的時間內發生了以下事情：

### 第一步：尋找地址 (DNS 解析)
電腦看不懂 `google.com` 這種文字，它只認得 IP 地址 (例如 `142.250.190.46`)。
- **DNS (Domain Name System)** 就像是網路的「電話簿」。
- 瀏覽器會詢問 DNS 伺服器：「請問 `google.com` 的 IP 是多少？」
- DNS 回覆：「它的 IP 是 `142.250.190.46`」。

### 第二步：建立連接 (TCP/TLS Handshake)
瀏覽器拿到 IP 後，會與該伺服器建立連接。
- 如果是 `https`，會進行 **TLS 握手** (Handshake)，確保你的數據在傳輸過程中被加密，不會被駭客偷看。

### 第三步：發送請求 (HTTP Request)
瀏覽器發送一個 HTTP 請求，告訴伺服器：「我想看你的首頁 (GET / index.html)」。

### 第四步：伺服器回應 (HTTP Response)
伺服器收到請求後，會從硬碟或資料庫中找出對應的內容，回傳一個 **HTTP 響應**。
- 如果成功，會回傳 `200 OK` 以及網頁內容 (HTML 程式碼)。
- 如果找不到，會回傳 `404 Not Found`。

### 第五步：瀏覽器渲染 (Rendering)
瀏覽器收到 HTML 後，開始解析並下載 CSS 和 JS，最後將其轉化為你看到的精美畫面。

---

## 3. 專業工程師的視角：HTTP 協議

作為工程師，你不需要背誦所有細節，但你必須知道 **HTTP (HyperText Transfer Protocol)** 是網頁傳輸的「語言」。

- **GET**：向伺服器「索取」資料 (例如：讀取 YouBike 站點清單)。
- **POST**：向伺服器「提交」資料 (例如：登入帳號、發布貼文)。
- **Headers (標頭)**：請求中的「額外資訊」。例如 `User-Agent` 告訴伺服器你是用 iPhone 還是 PC 訪問，`Accept-Language` 告訴伺服器你想要中文還是英文界面。

---

## 🛠️ 實作挑戰：觀察你的第一個 Request

1. 打開任何一個網頁 (例如 Google)。
2. 按下 **F12** $\rightarrow$ 切換到 **Network (網路)** 分頁。
3. 重新整理頁面 (F5)。
4. 點擊列表中的第一個請求 (通常是域名本身)，查看右側的 **Headers**。
5. **找出以下資訊：**
   - Request URL (請求網址) 是什麼？
   - Status Code (狀態碼) 是多少？ (應該是 200)
   - Response Headers 裡的 `Content-Type` 是什麼？ (應該是 `text/html`)

**完成這個挑戰，你才真正理解了網頁是如何「運作」的。**

---

<p align="center">
<a href="00-How-to-Study.md">00-How-to-Study ⬅️</a> &nbsp; | &nbsp; <a href="02-html-css-js-intro.md">02-html-css-js-intro ➡️</a>
</p>