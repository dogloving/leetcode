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
var isSymmetric = function(root) {
    if (!root) return true
    let in_left = [], in_right = [], pre_left = [], pre_right = []
    inOrder1(root.left,in_left)
    inOrder2(root.right,in_right)
    preOrder1(root.left,pre_left)
    preOrder2(root.right,pre_right)
    console.log(in_left,in_right)
    return (in_left.toString()==in_right.toString())&&(pre_left.toString()==pre_right.toString())
};

function inOrder1(node, arr) {
    if (!node) return
    if (node.left) {
        arr.push('A')
        inOrder1(node.left,arr)
    }
    arr.push(node.val)
    if (node.right) {
        arr.push('B')
        inOrder1(node.right,arr)
    }
}
function inOrder2(node, arr) {
    if (!node) return
    if (node.right) {
        arr.push('A')
        inOrder2(node.right,arr)
    }
    arr.push(node.val)
    if (node.left) {
        arr.push('B')
        inOrder2(node.left,arr)
    }
}
function preOrder1(node, arr) {
    if (!node) return
    arr.push(node.val)
    if (node.left) {
        arr.push('A')
        preOrder1(node.left,arr)
    }
    if (node.right) {
        arr.push('B')
        preOrder1(node.right,arr)
    }
}
function preOrder2(node, arr) {
    if (!node) return
    arr.push(node.val)
    if (node.right) {
        arr.push('A')
        preOrder2(node.right,arr)
    }
    if (node.left) {
        arr.push('B')
        preOrder2(node.left,arr)
    }
}
```

思路：先序遍历和中序遍历可以确定一颗二叉树。但是当树中有相同值结点时，该方法不奏效。因此还需要通过一定手段确定树的结构。上面是差的方法，下面是好方法：

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
var isSymmetric = function(root) {
    if (!root) return true
    return helper(root.left,root.right)
};

function helper(left,right) {
    if (!left&&!right) return true
    if (!left||!right) return false
    return (left.val==right.val)&&helper(left.left,right.right)&&helper(left.right,right.left)
}
```

