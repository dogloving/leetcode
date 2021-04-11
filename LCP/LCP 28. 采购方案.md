```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var purchasePlans = function(nums, target) {
    nums.sort((a,b)=>a-b)
    let M = 1e9+7
    let res = 0
    let l = 0, r = nums.length-1
    while (l<r) {
        if (nums[l]+nums[r]<=target) {
            res += (r-l)
            l++
        } else r--
    }
    return res%M
};
```

思路：