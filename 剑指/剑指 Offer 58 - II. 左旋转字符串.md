```javascript
/**
 * @param {string} s
 * @param {number} n
 * @return {string}
 */
var reverseLeftWords = function(s, n) {
    n %= s.length
    return s.substr(n)+s.substr(0,n)
};
```

