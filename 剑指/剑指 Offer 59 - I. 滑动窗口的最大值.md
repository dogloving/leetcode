```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var maxSlidingWindow = function(nums, k) {
    if (nums.length==0) return []
    let queue = [0]
    for (let i = 1; i < k; i++) {
        while (nums[i]>=nums[queue[queue.length-1]]) queue.pop()
        queue.push(i)
    }
    let res = [nums[queue[0]]]
    for (let i = k; i < nums.length; i++) {
        if (queue[0]==i-k) queue.shift()
        while (nums[i]>=nums[queue[queue.length-1]]) queue.pop()
        queue.push(i)
        res.push(nums[queue[0]])
    }
    return res
};
```

思路：同239.维护一个单调队列。