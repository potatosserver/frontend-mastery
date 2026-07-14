# 解答：05. 語義化與無障礙

### 實作目標
將整個主專案的 `div` 結構重構為語義化標籤。

### 專業代碼實現
```html
<!-- 之前使用 <div id="header"> 改為 -->
<header>
    <nav>...</nav>
</header>

<!-- 之前使用 <div id="main"> 改為 -->
<main>
    <section id="about">...</section>
    <section id="works">
        <article>...</article>
    </section>
</main>

<!-- 之前使用 <div id="footer"> 改為 -->
<footer>
    <p>&copy; 2026 Your Name</p>
</footer>
```

### 設計意圖
- 使用 `<main>` 標記頁面核心內容 (每頁唯一)。
- 使用 `<article>` 包裹每個獨立的作品項目，使其在邏輯上可獨立存在。
- 使用 `<nav>` 標記導航區，讓爬蟲快速索引連結。
