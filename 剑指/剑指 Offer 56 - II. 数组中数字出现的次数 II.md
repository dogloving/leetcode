```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    let res = 0
    for (let bit = 0; bit<32; bit++) {
        let cnt1 = 0
        for (let num of nums) cnt1 += ((num>>bit)&1)
        if (cnt1%3) res += (1<<bit)
    }
    return res
};
```

思路：同leetcode137