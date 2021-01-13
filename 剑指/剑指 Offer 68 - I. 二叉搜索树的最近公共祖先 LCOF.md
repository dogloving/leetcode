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
    dfs(root,Math.min(p.val,q.val),Math.max(p.val,q.val))
    return res

    function dfs(node,min,max) {
        if (!node) return
        if (node.val>=min&&node.val<=max) {
            res = node
            return
        } else if (node.val<min) dfs(node.right,min,max)
        else dfs(node.left,min,max)

    }
};
```