# 解答：03. 表單與輸入元件

### 實作目標
在主專案中實作一個專業的聯絡表單。

### 專業代碼實現
```html
<section id="contact">
    <h2>聯絡我</h2>
    <form action="#" method="POST">
        <div class="form-group">
            <label for="name">姓名：</label>
            <input type="text" id="name" name="name" required minlength="2">
        </div>
        <div class="form-group">
            <label for="email">電子郵件：</label>
            <input type="email" id="email" name="email" required>
        </div>
        <div class="form-group">
            <label for="msg">訊息：</label>
            <textarea id="msg" name="msg" rows="5" required></textarea>
        </div>
        <button type="submit">發送訊息</button>
    </form>
</section>
```

### 設計意圖
- 每個 input 必須對應一個 `<label>`，提升 A11y。
- 使用 `type="email"` 利用瀏覽器原生驗證降低錯誤率。
- 使用 `required` 強制必填，減少伺服器端處理無效數據的壓力。
