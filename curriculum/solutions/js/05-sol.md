# 解答：05. 陣列與物件剖析

### 實作目標
實作作品集動態篩選。

### 專業實現
```javascript
const projects = [{title:'A', cat:'HTML'}, {title:'B', cat:'CSS'}];
const filtered = projects.filter(p => p.cat === 'HTML');
const html = filtered.map(p => `<li>${p.title}</li>`).join('');
document.querySelector('.grid').innerHTML = `<ul>${html}</ul>`;
```