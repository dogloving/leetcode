```js
/**
 * @param {number} n
 * @param {number} k
 * @return {number}
 */
var paintingPlan = function(n, k) {
    if (n*n==k) return 1
    let res = 0
    for (let row = 0; row < n; row++) {
        for (let col = 0; col < n; col++) {
            if ((row*n+col*n-row*col)==k) res += Cn(row)*Cn(col)
        }
    }
    return res

    function Cn(x) {
        if (x==0) return 1
        let r = 1
        for (let i = n; i > n-x; i--) r *= i
        for (let i = 1; i <= x; i++) r /= i
        return r
    }
};
```

