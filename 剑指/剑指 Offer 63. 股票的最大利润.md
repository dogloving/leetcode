```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    let res = 0
    let buy = 999999999
    for (let p of prices) {
        if (p<buy) buy = p
        else res = Math.max(res,p-buy) 
    }
    return res
};
```

