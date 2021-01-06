```javascript
/**
 * @param {number[]} postorder
 * @return {boolean}
 */
var verifyPostorder = function(postorder) {
    if (postorder.length<=2) return true
    let root_val = postorder[postorder.length-1]
    let idx = postorder.length-1
    for (let i = 0; i < postorder.length-1; i++) {
        if (postorder[i]>root_val) {
            idx = i
            break
        }
    }
    // 检查后面
    for (let i = idx; i < postorder.length-1; i++) {
        if (postorder[i]<root_val) return false
    }
    return verifyPostorder(postorder.slice(0,idx))&&verifyPostorder(postorder.slice(idx,postorder.length-1))
};
```

思路：首先最后一个是根节点，然后比根节点大的在右边，比根节点小的在左边。递归判断。