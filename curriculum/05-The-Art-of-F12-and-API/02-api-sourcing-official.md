# 02. 官方 API 獲取 (API Sourcing Official)

在掌握了 F12 的基本操作後，接下來我們要學習如何獲取數據。最正規、最穩定的方式就是使用 **官方 API (Official API)**。

---

## 1. 什麼是 API 接口？

API (Application Programming Interface) 就像是伺服器提供給開發者的「服務窗口」。你發送一個請求，伺服器根據規則回傳數據。

**🚀 官方 API 的特點：**
- **穩定**：只要官方不更新版本，接口路徑不會變。
- **權限控制**：通常需要 **API Key** (就像是一把鑰匙) 才能訪問。
- **文檔完整**：官方會提供詳細的 API Document 告訴你怎麼用。

---

## 2. 獲取 API Key 的標準流程

大多數專業 API (如 Google Maps, OpenAI, GitHub API) 遵循以下流程：
1. **註冊帳號** $\rightarrow$ 進入 Developer Portal。
2. **建立 Application** $\rightarrow$ 取得唯一的 `Client ID` 與 `Secret Key`。
3. **設定權限 (Scopes)** $\rightarrow$ 決定你的 Key 能讀取哪些數據。
4. **保管 Key** $\rightarrow$ **絕對禁止將 API Key 直接寫在前端代碼中並上傳到 GitHub** $\rightarrow$ 這會導致你的帳號被盜用。

---

## 3. 實作請求：使用 Fetch API

假設我們要從一個公開的 API 獲取數據。

**🚀 實作範例：**
```javascript
async function getData() {
    try {
        const response = await fetch('https://api.example.com/data?apikey=YOUR_KEY');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("獲取失敗:", error);
    }
}
getData();
```

---

## 🛠️ 實作挑戰

1. **註冊 API**：嘗試去註冊一個免費的 API (例如 OpenWeatherMap 或 GitHub API)。
2. **測試請求**：使用 F12 的 Network Tab $\rightarrow$ 發送請求 $\rightarrow$ 確認 Response 是正確的 JSON 格式。
3. **驗證 Key**：嘗試刪除 API Key 的其中一個字符 $\rightarrow$ 觀察伺服器回傳的 `401 Unauthorized` 錯誤。

---
<p align="center">
<a href="01-f12-mastery.md">01-f12-mastery ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/f12/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-api-reverse-engineering.md">03-api-reverse-engineering ➡️</a>
</p>
