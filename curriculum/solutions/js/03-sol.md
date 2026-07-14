# 解答：03. 函數與作用域

### 實作目標
實作私有計數器閉包。

### 專業實現
```javascript
function createCounter() {
    let count = 0;
    return () => ++count;
}
const counter = createCounter();
print(counter()); // 1
print(counter()); // 2
```