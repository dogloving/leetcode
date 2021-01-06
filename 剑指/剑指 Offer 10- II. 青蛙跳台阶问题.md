```javascript
/**
 * @param {number} n
 * @return {number}
 */
var numWays = function(n) {
    if (n==0) return 1
    let M = 1e9+7
    let dp = [1,2]
    for (let i = 2; i < n; i++) {
        dp[i] = dp[i-1]+dp[i-2]
        dp[i] %= M
    }
    return dp[n-1]
};
```

