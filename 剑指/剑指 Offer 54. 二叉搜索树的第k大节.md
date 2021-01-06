```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} k
 * @return {number}
 */
var kthLargest = function(root, k) {
    let res = null, i = 0
    post(root)
    return res

    function post(node) {
        if (!node) return
        post(node.right)
        if (k==1) {
            res = node.val
            k--
            return
        }
        if (k<=0) return
        k--
        post(node.left)
    }
};
```

