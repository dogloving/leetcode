```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
var getIntersectionNode = function(headA, headB) {
    let l1 = 0, l2 = 0
    let node = headA
    while (node&&++l1) node = node.next
    node = headB
    while (node&&++l2) node = node.next
    let nodeA = headA, nodeB = headB
    while (l1>l2&&l1--) nodeA = nodeA.next
    while (l1<l2&&l2--) nodeB = nodeB.next
    while (nodeA&&nodeB&&nodeA!=nodeB) {
        nodeA = nodeA.next
        nodeB = nodeB.next
    }
    return nodeA
};
```

