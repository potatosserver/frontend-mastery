# 解答：07. 引擎與事件循環

### 實作目標
驗證微任務優先級。

### 專業實現
```javascript
console.log('1');
setTimeout(() => console.log('2'), 0);
Promise.resolve().then(() => console.log('3'));
console.log('4');
// 預期輸出: 1, 4, 3, 2
```