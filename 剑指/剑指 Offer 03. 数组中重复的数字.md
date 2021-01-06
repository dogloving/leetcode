```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findRepeatNumber = function(nums) {
    for (let num of nums) if (nums.indexOf(num)!=nums.lastIndexOf(num)) return num
};
```

