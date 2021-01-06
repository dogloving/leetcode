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
 * @return {number[]}
 */
var levelOrder = function(root) {
    if (!root) return []
    let res = []
    let q = [root]
    while (q.length) {
        let node = q[0]
        q.shift()
        res.push(node.val)
        if (node.left) q.push(node.left)
        if (node.right) q.push(node.right)
    }
    return res
};
```

