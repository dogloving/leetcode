```javascript
// 模拟
/**
 * @param {number} n
 * @param {number} m
 * @return {number}
 */
var lastRemaining = function(n, m) {
    let res = []
    for (let i = 0; i < n; i++) res.push(i)
    let idx = 0
    while (res.length>1) {
        idx = (idx+m-1+res.length)%res.length
        res = res.slice(0,idx).concat(res.slice(idx+1))
    }
    return res[0]
};

// 反推
/**
 * @param {number} n
 * @param {number} m
 * @return {number}
 */
var lastRemaining = function(n, m) {
    let res = 0
    for (let i = 2; i <= n ;i++) res = (res+m)%i
    return res
};
```

思路：模拟会超时，因为每次需要删除一个元素构建新数组，用时O(n).

反推：见https://leetcode-cn.com/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/solution/javajie-jue-yue-se-fu-huan-wen-ti-gao-su-ni-wei-sh/