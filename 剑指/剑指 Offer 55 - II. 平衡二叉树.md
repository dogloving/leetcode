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
 * @return {boolean}
 */
var isBalanced = function(root) {
    if (!root) return true
    let left = helper(root.left)
    if (!left[0]) return false
    let right = helper(root.right)
    if (!right[0]) return false
    return Math.abs(left[1]-right[1])<=1
};
function helper(node) {
    if (!node) return [true,0]
    let left = helper(node.left)
    if (!left[0]) return [false,0]
    let right = helper(node.right)
    if (!right[0]) return [false,0]
    return [Math.abs(left[1]-right[1])<=1,Math.max(left[1],right[1])+1]
}
```

