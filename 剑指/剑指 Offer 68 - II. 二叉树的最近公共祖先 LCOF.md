```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function(root, p, q) {
    let res = null
    post(root)
    return res

    function post(node) {
        if (!node) return false
        let left = post(node.left)
        if (res) return true
        if (left&&(p==node||q==node)) {
            res = node
            return true
        }
        let right = post(node.right)
        if (res) return true
        if (right&&(p==node||q==node)) {
            res = node
            return true
        }
        if (left&&right) {
            res = node
            return true
        }
        return left||right||p==node||q==node
    }
};
```

