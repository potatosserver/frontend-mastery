# 解答：02. 文字與基礎標標籤

### 實作目標
在主專案中建立 Hero Section 與自我介紹區塊。

### 專業代碼實現
```html
<header>
    <h1>你好，我是 [你的名字]</h1>
    <p>一名專注於 <strong>極簡主義</strong> 與 <strong>高性能</strong> 的前端開發工程師。</p>
    <a href="#works">查看我的作品</a>
</header>

<section id="about">
    <h2>關於我</h2>
    <p>我熱愛將複雜的邏輯轉化為簡單的介面。目前我正在學習：</p>
    <ul>
        <li>HTML5 語義化</li>
        <li>CSS3 響應式佈局</li>
        <li>JavaScript 異步開發</li>
    </ul>
</section>
```

### 設計意圖
- 使用 `<h1>` 定義頁面唯一主標題。
- 使用 `<ul>` 組織技能列表，增加可讀性。
- 使用 `<strong>` 突出核心競爭力。
