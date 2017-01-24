# Problem Describe:
<pre>	
Given a linked list, determine if it has a cycle in it.

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
    bool hasCycle(ListNode *head) {
        ListNode *fast=head,*slow=head;
        while(fast && slow && fast->next)
        {
            fast=fast->next->next;
            slow=slow->next;
            if(slow==fast)return true;
        }
        return false;
    }
};
</pre>
# 思路：
这题有一个比较暴力的解法，就是在一个较大的循环中不断的使head=head->next,如果head为NULL就返回false，如果循环结束还没NULL，说明是个cycle，返回true，当然前提是这个循环次数比较多，比如99999这种。
这里另一种解法是使用快慢指针，每次令一个指针向前跳两个节点，另一个指针向前跳一个节点，如果是cycle那么fast指针必定会“追上”slow指针。快慢指针是这类题常用的一个方法。