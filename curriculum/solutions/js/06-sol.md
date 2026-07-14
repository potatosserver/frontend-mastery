# 解答：06. 異步與 Promise

### 實作目標
串接 API 顯示金句。

### 專業實現
```javascript
async function load() {
    try {
        const res = await fetch('https://api.quotable.io/random');
        const data = await res.json();
        document.querySelector('#q').innerText = data.content;
    } catch(e) { console.error(e); }
}
load();
```