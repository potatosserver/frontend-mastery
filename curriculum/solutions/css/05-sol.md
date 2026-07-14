# 解答：05. Grid 實作

### 實作目標
打造響應式作品集卡片牆 (Works Gallery)。

### 專業代碼實現
```css
.works-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 30px;
    padding: 20px;
}

.work-item {
    display: flex;
    flex-direction: column;
    background: white;
    border-radius: 16px;
    overflow: hidden;
    transition: transform 0.3s ease;
}

.work-item:hover {
    transform: translateY(-10px);
}
```

### 設計意圖
- `repeat(auto-fill, minmax(300px, 1fr))` 是工業標準，讓卡片數目隨寬度自動調整而無需 Media Query。
- `overflow: hidden` 配合 `border-radius` 確保圖片圓角正確切除。
- `transform: translateY` 增加互動反饋，提升視覺品質。
