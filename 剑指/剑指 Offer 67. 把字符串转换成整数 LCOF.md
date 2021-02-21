```js
/**
 * @param {string} str
 * @return {number}
 */
var strToInt = function(str) {
    let max = Math.pow(2,31)-1, min = Math.pow(2,31)
    let res = 0
    let idx = 0
    while (idx<str.length) {
        if (/[\s0-9+-]/.test(str[idx])==false) return 0
        else if (/[0-9+-]/.test(str[idx])) break
        idx++
    }
    if (idx==str.length) return 0
    let neg = false
    if (str[idx]=='-') neg = true
    else if (str[idx]!='+') res = res*10+(str[idx].charCodeAt()-'0'.charCodeAt())
    idx++
    while (idx<str.length) {
        if (/[0-9]/.test(str[idx])==false) break
        res = res*10+(str[idx].charCodeAt()-'0'.charCodeAt())
        idx++
        if (neg&&res>min) return -min
        else if (!neg&&res>max) return max
    }
    if (neg&&res>min) return -min
    else if (!neg&&res>max) return max
    if (neg) res *= -1
    return res
};
```

