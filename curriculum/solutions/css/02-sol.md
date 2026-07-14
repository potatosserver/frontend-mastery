# 解答：02. 盒模型與單位

### 實作目標
設定 Hero Section 與 About Section 的間距與尺寸。

### 專業代碼實現
```css
.hero-section {
    padding: 80px 20px;
    max-width: 1100px;
    margin: 0 auto;
    text-align: center;
}

.about-card {
    background: white;
    padding: 2rem;
    border-radius: 12px;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
    margin-bottom: 2rem;
}
```

### 設計意圖
- 使用 `margin: 0 auto` 實現水平居中。
- 使用 `rem` 單位而非 `px`，確保字體與間距隨根元素縮放 (A11y)。
- 使用 `box-shadow` 創造層次感，避免頁面顯得太扁平。
