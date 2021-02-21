```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} A
 * @param {TreeNode} B
 * @return {boolean}
 */
var isSubStructure = function(A, B) {
    if (B==null||A==null) return false
    if (A.val==B.val&&helper(A,B)) return true
    return isSubStructure(A.left,B)||isSubStructure(A.right,B)

    function helper(a,b) {
        if (b==null) return true
        if (a==null) return false
        if (a.val!=b.val) return false
        return helper(a.left,b.left)&&helper(a.right,b.right)
    }
};
```

