```javascript
/**
 * @param {number} target
 * @return {number[][]}
 */
var findContinuousSequence = function(target) {
    let res = []
    let l = 1, r = 1
    let sum = 1, window = [1]
    while (r<target) {
        if (sum==target) {
            res.push(window.slice())
            window.push(++r)
            sum += r
        } else if (sum<target) {
            window.push(++r)
            sum += r
        } else {
            window.shift()
            sum -= (l++)
        }
    }
    return res
};
```

思路：滑动窗口。