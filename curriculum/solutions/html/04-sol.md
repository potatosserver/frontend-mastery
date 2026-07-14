# 解答：04. 多媒體與表格

### 實作目標
在主專案中建立作品展示區 (Works Gallery) 與技術對比表。

### 專業代碼實現
```html
<section id="works">
    <h2>我的作品集</h2>
    <div class="works-grid">
        <article>
            <img src="project1.jpg" alt="即時交通查詢網頁 - 簡潔的藍色調介面">
            <h3>交通查詢工具</h3>
            <p>實現了即時數據串接與地理定位功能。</p>
        </article>
    </div>
</section>

<section id="specs">
    <h3>技術規格對比</h3>
    <table>
        <thead>
            <tr>
                <th>技術</th>
                <th>學習難度</th>
                <th>重要程度</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>HTML</td>
                <td>低</td>
                <td>極高</td>
            </tr>
            <tr>
                <td>CSS Grid</td>
                <td>中</td>
                <td>高</td>
            </tr>
        </tbody>
    </table>
</section>
```

### 設計意圖
- `img` 必須包含 `alt` 描述，以支持螢幕閱讀器與 SEO。
- 表格使用 `<thead>` 和 `<tbody>` 分離，增加結構清晰度。
