# Problem Describe:
<pre>
	Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

	Note: Do not modify the linked list.

	Follow up:
	Can you solve it without using extra space?
</pre>
# My Code:
<pre>
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
    ListNode *detectCycle(ListNode *head) {
        ListNode *fast=head,*slow=head;
        while(fast && slow && fast->next)
        {
            fast=fast->next->next;
            slow=slow->next;
            if(fast==slow)
            {
                while(slow!=head)
                {
                    slow=slow->next;
                    head=head->next;
                }
                return head;
            }
        }
        return NULL;
    }
};
</pre>
# 思路：
这题在于理解题意：并不一定是整条链表形成一个环，也可能是一个环带个小尾巴。知道了这点就豁然开朗了，解法基本同上题。

