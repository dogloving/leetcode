```javascript
/**
 * @param {number[]} pushed
 * @param {number[]} popped
 * @return {boolean}
 */
var validateStackSequences = function(pushed, popped) {
    let idx_push = 0, idx_pop = 0
    let stack = []
    while (idx_pop<popped.length) {
        if (stack.length==0) stack.push(pushed[idx_push++])
        else {
            if (popped[idx_pop]==stack[stack.length-1]) {
                stack.pop()
                idx_pop++
            } else {
                if (idx_push==pushed.length) return false
                stack.push(pushed[idx_push++])
            }
        }
    }
    return true
};
```

