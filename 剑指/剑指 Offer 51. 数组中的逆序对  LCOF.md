```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var reversePairs = function(nums) {
    let res = 0
    merge(0,nums.length-1)
    return res

    function merge(l,r) {
        if (l>=r) return
        let m = (l+r)>>1
        merge(l,m)
        merge(m+1,r)
        let i1 = l, i2 = m+1
        let arr = []
        while (i1<=m&&i2<=r) {
            while (i2<=r&&nums[i1]>nums[i2]) arr.push(nums[i2++])
            res += (i2-m-1)
            arr.push(nums[i1++])
        }
        while (i1<=m) {
            res += (r-m)
            arr.push(nums[i1++])
        }
        while (i2<=r) arr.push(nums[i2++])
        let i = 0
        for (let j = l; j <= r;) nums[j++] = arr[i++]
    }

};
```

思路：

1. 方法一：维护一个有序队列。使用二分法查找。由于插入需要移动，时间复杂度O(n^2)，但优于暴力。
2. 方法二：归并。O(nlogn)