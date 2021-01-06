```javascript
/**
 * @param {string} s
 * @return {number}
 */
var calculate = function(s) {
    let res = 0
    let x = 1, y = 0
    for (let c of s) {
        if (c=='A') x = x*2+y
        else y = y*2+x
    }
    return x+y
};
```

