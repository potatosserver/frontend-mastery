# 解答：04. Flexbox 實戰

### 實作目標
打造專業的導航欄連結分佈與 Hero Section 的元素對齊。

### 專業代碼實現
```css
.nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
}

.hero-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    min-height: 80vh;
}

.hero-btns {
    display: flex;
    gap: 1rem;
    margin-top: 2rem;
}
```

### 設計意圖
- `gap` 屬性簡化了間距管理，不再需要寫 `.item:last-child { margin: 0 }`。
- `flex-direction: column` 讓 Hero Section 在手機端能快速切換對齊方式。
- `justify-content: center` 實現完美的水平垂直居中。
