```javascript
/**
 * @param {number} num
 * @return {number}
 */
var translateNum = function(num) {
    num = num.toString()
    let res = 0
    dfs(0)
    return res

    function dfs(idx) {
        if (idx>=num.length) res += 1
        else if (idx==num.length-1) res += 1
        else {
            if (parseInt(num.substr(idx,2))<=25&&num[idx]!='0') {
                dfs(idx+1)
                dfs(idx+2)
            } else dfs(idx+1)
        }
    }
};
```

