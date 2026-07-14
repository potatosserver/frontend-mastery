# 03. REST vs GraphQL (數據接口之爭)

當你的專案變大時，你會發現單純的 `GET /users` 已經不能滿足需求。如果你只需要使用者的「姓名」，但伺服器卻回傳了 50 個欄位（包含地址、電話、生日...） $\rightarrow$ 這就是 **Over-fetching (過度獲取)** $\rightarrow$ 浪費流量且降低速度。

為了解決這個問題，業界出現了兩種主流的接口設計哲學：**REST** 與 **GraphQL**。

---

## 📜 起源：從資源到查詢

- **REST (Representational State Transfer)** $\rightarrow$ 這是目前的工業標準。它的核心是 **「資源 (Resource)」** $\rightarrow$ 每個 URL 代表一個資源 (例如 `/users/1`) $\rightarrow$ 使用標準的 HTTP 方法 (GET, POST, PUT, DELETE) 操作。
- **GraphQL (Graph Query Language)** $\rightarrow$ 由 Facebook 推出。它的核心是 **「查詢 (Query)」** $\rightarrow$ 只有一個入口 (例如 `/graphql`) $\rightarrow$ 客戶端告訴伺服器：「我只要-名字-和-頭像」，伺服器就只回傳這兩個欄位。

---

## 1. 視覺化對比：獲取一個使用者及其所有作品

**🚀 REST 模式 (多次請求)**：
1. 請求 `GET /users/1` $\rightarrow$ 得到使用者 ID $\rightarrow$ 發現他有 3 個作品 ID。
2. 請求 `GET /projects/1` $\rightarrow$ 得到第一個作品詳細資料。
3. 請求 `GET /projects/2` $\rightarrow$ 得到第二個... (重複 3 次)。
**結果**：發送了 4 次請求 $\rightarrow$ 延遲增加 $\rightarrow$ 體驗下降。

**✅ GraphQL 模式 (單次請求)**：
發送一個查詢：
```graphql
{
  user(id: 1) {
    name
    projects {
      title
      url
    }
  }
}
```
**結果**：一次請求 $\rightarrow$ 直接拿到所有需要的結構化數據 $\rightarrow$ 速度極快。

---

## 2. 如何選擇？ (Decision Matrix)

沒有絕對的贏家，只有適合的場景：

| 特性 | REST | GraphQL |
| :--- | :--- | :--- |
| **學習曲線** | 極低 (簡單 URL) | 較高 (需學習 Schema 語法) |
| **快取效能** | 極強 (利用瀏覽器 HTTP 快取) | 較弱 (通常是 POST 請求，難以快取) |
| **數據精確度** | 低 (容易 Over-fetching) | 極高 (按需獲取) |
| **適用場景** | 簡單 API、公開接口、快取要求高 | 複雜數據關聯、行動端 APP (流量敏感) |

---

## 🛠️ 接口設計挑戰

1. **設計 REST 路由** $\rightarrow$ 假設你要做一個「作品集管理系統」 $\rightarrow$ 定義獲取、新增、修改、刪除作品的 URL 與 HTTP 方法。
2. **撰寫 GraphQL 查詢** $\rightarrow$ 練習編寫一個查詢 $\rightarrow$ 獲取「所有類別為 Frontend 的作品」及其「作者姓名」。
3. **分析 Payload** $\rightarrow$ 使用 F12 Network Tab $\rightarrow$ 找一個使用 GraphQL 的網站 (例如 GitHub API) $\rightarrow$ 觀察其請求體與回傳結果。

---
<p align="center">
<a href="02-security-hardening.md">02-security-hardening ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/net/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-realtime-comm.md">04-realtime-comm ➡️</a>
</p>
