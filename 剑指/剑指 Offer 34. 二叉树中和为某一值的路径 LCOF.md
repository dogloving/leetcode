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
 * @param {number} sum
 * @return {number[][]}
 */
var pathSum = function(root, sum) {
    if (!root) return []
    let res = []
    helper(root,[],0)
    return res

    function helper(node, arr, s) {
        arr.push(node.val)
        s += node.val
        if (!node.left&&!node.right) {
            if (s==sum) res.push(arr.slice())
        }
        if (node.left) helper(node.left,arr,s)
        if (node.right) helper(node.right,arr,s)
        arr.pop()
    }


};
```

