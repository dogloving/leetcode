```js
var dicesProbability = function(n) {
    let point_cnt = new Map()
    for (let point = 1; point <= 6; point++) point_cnt.set(point, 1)
    for (let cnt = 2; cnt <= n; cnt++) {
        let tmp = new Map()
        for (let point = 1; point <= 6; point++) {
            for (let p of Array.from(point_cnt.keys())) {
                if (tmp.has(p+point)) tmp.set(p+point, tmp.get(p+point)+point_cnt.get(p))
                else tmp.set(p+point, point_cnt.get(p))
            }
        }
        point_cnt = tmp
    }
    let res = []
    for (let point = n; point <= n*6; point++) {
        res.push(point_cnt.get(point)/Math.pow(6,n))
    }
    return res
};
```

思路：递推。

```js
var dicesProbability = function(n) {
    let dp = new Array(n+1).fill(null).map(d=>new Array(n*6+1).fill(0))
    for (let j = 1; j <= 6; j++) dp[1][j] = 1
    for (let i = 2; i <= n; i++) {
        for (let j = i; j <= i*6; j++) {
            for (let p = 1; p<=6&&j-p>=1; p++) {
                dp[i][j] += dp[i-1][j-p]
            }
        }
    }
    let res = []
    for (let j = n; j <= n*6; j++) res.push(dp[n][j]/Math.pow(6,n))
    return res
};
```

思路：动态规划。令dp[i] [j]表示扔了i次后，点数j出现次数。