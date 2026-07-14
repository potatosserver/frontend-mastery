# 解答：01. 簡介與選擇器

### 實作目標
為主專案設定全站基礎配色、字體與基本排版。

### 專業代碼實現
```css
:root {
    --primary-color: #2563eb;
    --text-main: #1f2937;
    --text-muted: #6b7280;
    --bg-light: #f9fafb;
}

* {
    box-sizing: border-box;
    margin: 0; 
    padding: 0;
}

body {
    font-family: 'Inter', sans-serif;
    color: var(--text-main);
    background-color: var(--bg-light);
    line-height: 1.6;
}

.highlight {
    color: var(--primary-color);
    font-weight: bold;
}
```

### 設計意圖
- 使用 `:root` 定義 CSS 變數，方便全站統一修改主題色。
- 使用 `* { box-sizing: border-box; }` 確保佈局不會因為 Padding 爆掉。
- 設定基礎 `line-height` 提升文字可讀性。
