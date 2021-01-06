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
 * @return {ListNode}
 */
var reverseList = function(head) {
    let res = null, last = null
    while (head) {
        let node = new ListNode(head.val)
        if (last!=null) node.next = last
        last = node
        if (head.next==null) res = node
        head = head.next
    }
    return res
};
```

