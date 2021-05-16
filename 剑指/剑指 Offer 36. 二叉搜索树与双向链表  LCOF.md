```js
var treeToDoublyList = function(root) {
    return helper(root)[0]

    function helper(node) {
        if (!node) return [null,null]
        let left = helper(node.left), right = helper(node.right)
        if (left[1]) {
            left[1].right = node
            node.left = left[1]
        }
        if (right[0]) {
            right[0].left = node
            node.right = right[0]
        }
        if (left[0]) {
            if (right[1]) {
                left[0].left = right[1]
                right[1].right = left[0]
            } else {
                left[0].left = node
                node.right = left[0]
            }
        } else {
            if (right[1]) {
                right[1].right = node
                node.left = right[1]
            } else {
                node.left = node
                node.right = node
            }
        }
        return [left[0]?left[0]:node, right[1]?right[1]:node]
    }
};
```

思路：采用后续遍历的思想。对于一个结点node，假设它的左边和右边都处理好了得到左右两条链表，那么通过把node插入到左右两条链表中间把它们连起来，然后返回当前链表的头结点和尾结点。