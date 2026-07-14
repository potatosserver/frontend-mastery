# 解答：03. 定位與 Z-Index

### 實作目標
實作固定頂部導航欄與浮動 action 按鈕。

### 專業代碼實現
```css
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 1000;
    background: rgba(255, 255, 255, 0.8);
    backdrop-filter: blur(10px);
    padding: 1rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.floating-btn {
    position: fixed;
    bottom: 30px;
    right: 30px;
    z-index: 99;
    padding: 15px 25px;
    border-radius: 50px;
    background: var(--primary-color);
    color: white;
}
```

### 設計意圖
- `position: fixed` 確保導航欄在滾動時依然可見。
- `backdrop-filter: blur` 營造現代感的玻璃擬態效果。
- `z-index: 1000` 確保導航欄永遠在最頂層。
