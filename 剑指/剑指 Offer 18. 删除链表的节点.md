```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* deleteNode(ListNode* head, int val) {
        while (head&&head->val==val) head = head->next;
        if (!head) return head;
        ListNode *pre = head, *node = head->next;
        while (node) {
            while (node&&node->val==val) node = node->next;
            pre->next = node;
            pre = node;
            if (node) node = node->next;
        }
        return head;
    }
};
```

