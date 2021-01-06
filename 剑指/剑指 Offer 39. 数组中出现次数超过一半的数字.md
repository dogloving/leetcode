```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    let num = nums[0], cnt = 1
    for (let i = 1; i < nums.length; i++) {
        if (nums[i]==num) cnt++
        else {
            cnt--
            if (cnt==-1) {
                num = nums[i]
                cnt = 1
            }
        }
    }
    return num
};
```

