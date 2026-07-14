# 解答：06. 響應式設計

### 實作目標
實作從手機到桌面的完整適應邏輯。

### 專業代碼實現
```css
/* Mobile First */
.navbar { padding: 1rem; }

@media (min-width: 768px) {
    .navbar { padding: 2rem 5rem; }
    .hero-container { 
        flex-direction: row; 
        text-align: left; 
    }
}

@media (min-width: 1200px) {
    .container { 
        max-width: 1200px; 
        margin: 0 auto; 
    }
}
```

### 設計意圖
- 採取 Mobile-First 策略，減少覆蓋代碼，提高加載速度。
- 使用 `min-width` 逐步增加複雜度 $\rightarrow$ 響應式斷點選擇 768px (平板) 與 1200px (桌面)。
- `margin: 0 auto` 確保大螢幕下內容不會過寬導致閱讀困難。
