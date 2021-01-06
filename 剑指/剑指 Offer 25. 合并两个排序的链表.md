```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    if (l1==null) return l2
    if (l2==null) return l1
    let head = null, pre = null
    while (l1&&l2) {
        let node = new ListNode()
        if (l1.val>l2.val) {
            node.val = l2.val
            l2 = l2.next
        } else {
            node.val = l1.val
            l1 = l1.next
        }
        if (head==null) head = node
        else pre.next = node
        pre = node
    }
    while (l1) {
        let node = new ListNode(l1.val)
        pre.next = node
        l1 = l1.next
        pre = node
    }
    while (l2) {
        let node = new ListNode(l2.val)
        pre.next = node
        l2 = l2.next
        pre = node
    }
    return head
};
```

