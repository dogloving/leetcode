```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {number[]} preorder
 * @param {number[]} inorder
 * @return {TreeNode}
 */
var buildTree = function(preorder, inorder) {
    if (preorder.length==0) return null
    let root_val = preorder[0]
    let idx = inorder.indexOf(root_val)
    let root = new TreeNode(root_val)
    root.left = buildTree(preorder.slice(1,idx+1),inorder.slice(0,idx))
    root.right = buildTree(preorder.slice(idx+1),inorder.slice(idx+1))
    return root
};
```

