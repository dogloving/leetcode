```javascript
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
    n = n.toString(2)
    let res = 0
    for (let c of n) res += (c=='1')
    return res
};
```

