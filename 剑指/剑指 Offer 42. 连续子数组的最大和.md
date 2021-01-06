```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    let res = nums[0]
    let sum = Math.max(0,nums[0])
    for (let i = 1; i < nums.length; i++) {
        let num = nums[i]
        sum += num
        res = Math.max(res,sum)
        if (sum<0) sum = 0
    }
    return res
};
```

