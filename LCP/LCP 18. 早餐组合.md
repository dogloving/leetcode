```js
/**
 * @param {number[]} staple
 * @param {number[]} drinks
 * @param {number} x
 * @return {number}
 */
var breakfastNumber = function(staple, drinks, x) {
    staple.sort((a,b)=>parseInt(a)-parseInt(b))
    drinks.sort((a,b)=>parseInt(a)-parseInt(b))
    let less = new Array(x).fill(0)
    let last = 0
    for (let d of drinks) {
        for (let i = last+1; i <= d; i++) less[i] = less[i-1]
        less[d]++
        last = d
    }
    for (let i = last+1; i < x; i++) less[i] = less[i-1]
    let M = 1e9+7
    let res = 0
    for (let s of staple) {
        if (s>=x) break
        res += less[x-s]
        res %= M
    }
    return res
};
```

思路：暴力双重循环容易超时。想到用空间换时间，数组less[i]表示小于等于i的有多少。