```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var singleNumbers = function(nums) {
    let Xor = 0
    for (let num of nums) Xor ^= num
    let mask = 1
    while ((mask&Xor)==0) mask<<=1
    let a = 0, b = 0
    for (let num of nums) {
        if (num&mask) a ^= num
        else b ^= num
    }
    return [a,b]
};
```

思路：

我们先对所有异或，结果XOr就是我们要找到两个只出现1次的数a和b的异或，即XOr=a^b。而且由于a!=b，因此XOr至少有一个bit为1.我们找到它为1的任意一个bit，令其为mask(说明这一个bit上a和b不相同)。现在我们通过mask将所有数分成两拨，一拨是该bit上为1的，另一拨是该bit上为0的，a和b肯定不在同一拨。由于两个相同的数肯定在同一拨，它们两两异或为0，因此最后两拨各自的异或结果为a和b。

同leetcode260