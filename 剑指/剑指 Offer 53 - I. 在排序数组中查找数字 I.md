```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    if (nums.length==0) return 0
    let l = 0, r = nums.length-1
    while (l<r) {
        let m = Math.floor((l+r)/2)
        if (nums[m]==target) return 1+search(nums.slice(l,m),target)+search(nums.slice(m+1,r+1),target)
        else if (nums[m]<target) l = m+1
        else r = m-1
    }
    return nums[l]==target?1:0
};
```

