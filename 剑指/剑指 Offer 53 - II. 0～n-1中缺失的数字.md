```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function(nums) {
    let n = nums.length
    return n*(n+1)/2-nums.reduce((a,b)=>a+b)
};
```

