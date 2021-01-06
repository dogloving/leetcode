```javascript
/**
 * @param {number} n
 * @return {number}
 */
var fib = function(n) {
    if (n<=1) return n
    let a = 0, b = 1
    let M = 1e9+7
    for (let i = 2; i <= n; i++) {
        [a,b] = [b,a+b]
        a %= M
        b %= M
    }
    return b
};
```

