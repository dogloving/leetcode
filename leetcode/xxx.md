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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if(!headA || !headB)return NULL;
        ListNode* pa=headA;
        ListNode* pb=headB;
        while(pa && pb && pa!=pb){
            pa=pa->next;
            pb=pb->next;
            if(pa==pb)return pa;
            if(pa==NULL)pa=headB;
            if(pb==NULL)pb=headA;
        }
        return pa;
    }
};
```

```js
```

