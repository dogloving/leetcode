```js
/**
 * @param {number[]} nums
 * @return {string}
 */
var minNumber = function(nums) {
    if (nums.length==1) return nums[0].toString()
    nums.sort((a,b)=>{return parseInt(a.toString()+b.toString())-parseInt(b.toString()+a.toString())})
    return nums.reduce((a,b)=>a.toString()+b.toString())
};
```

