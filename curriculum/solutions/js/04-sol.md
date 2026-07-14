# 解答：04. DOM 操作精通

### 實作目標
實作主題切換功能。

### 專業實現
```javascript
const btn = document.querySelector('#theme-toggle');
btn.addEventListener('click', () => {
    document.body.classList.toggle('dark-mode');
});
```