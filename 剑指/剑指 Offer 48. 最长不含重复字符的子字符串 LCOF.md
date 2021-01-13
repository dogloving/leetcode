```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    if (s.length==0) return 0
    let res = 1
    let start = 0
    let last = {}
    last[s[0]] = 0
    for (let i = 1; i < s.length; i++) {
        if ((s[i] in last)&&(last[s[i]]>=start)) start = last[s[i]]+1
        else res = Math.max(res,i-start+1)
        last[s[i]] = i
    }
    return res
};
```

