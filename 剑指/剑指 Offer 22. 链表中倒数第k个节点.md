```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} k
 * @return {ListNode}
 */
var getKthFromEnd = function(head, k) {
    let node = head
    for (let i = 1; i <= k; i++) node = node.next
    while (node) {
        node = node.next
        head = head.next
    }
    return head
};
```

