```js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var isStraight = function(nums) {
    nums.sort((a,b)=>parseInt(a)-parseInt(b))
    let min = 14, max = -1
    let cnt0 = 0
    for (let i = 0; i < 5; i++) {
        if (i>=1&&nums[i]==nums[i-1]&&nums[i]!=0) return false
        if (nums[i]!=0) {
            min = Math.min(min,nums[i])
            max = Math.max(max,nums[i])
        }
    }
    return max-min<=4
};
```

