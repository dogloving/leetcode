```javascript
/**
 * @param {number[]} coins
 * @return {number}
 */
var minCount = function(coins) {
    let res = 0
    for (let coin of coins) res += Math.floor((coin+1)/2)
    return res
};
```

