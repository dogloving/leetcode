```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    let cnt = new Array(1000001).fill(0)
    for (let num of nums) cnt[num]++
    for (let a = 1; a <= 1000000; a++) {
        let b = target-a
        cnt[a]--
        cnt[b]--
        if (cnt[a]>=0&&cnt[b]>=0) return [a,b]
        cnt[a]++
        cnt[b]++
    }
};
```

