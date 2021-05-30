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

思路：算出链表A和链表B分别的长度l1和l2，然后重新遍历两条链表。先让长的那条往前走abs(l1-l2)个结点，再一起往前走，直到结点一致。

```js
var getIntersectionNode = function(headA, headB) {
    let node1 = headA, node2 = headB;
    while (true) {
      if (node1===node2) return node1;
      if (node1===null) node1 = headB;
      else node1 = node1.next;
      if (node2===null) node2 = headA;
      else node2 = node2.next;
    }
};
```

思路：假设在链表A后面接一条链表B，在链表B后面接一条链表A，然后node1和node2分别遍历两条链表，由于现在后面“接上了”另一条链表的两条链表长度一致，因此如果存在公共结点，那么二者一定会在同一结点处相遇。
