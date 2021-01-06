```javascript
/**
 * @param {number[]} a
 * @return {number[]}
 */
var constructArr = function(a) {
    let cnt0 = 0, p = 1
    for (let num of a) {
        if (num==0) cnt0++
        else p *= num
    }
    if (cnt0 > 1) return new Array(a.length).fill(0)
    else {
        let res = []
        for (let num of a) {
            if (num==0) res.push(p)
            else if (cnt0==1) res.push(0)
            else res.push(p/num)
        }
        return res
    }
};
```

思路：要考虑到0的情况。