# Problem Describe:
<pre>
	Write a program to find the node at which the intersection of two singly linked lists begins.


For example, the following two linked lists:

A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
begin to intersect at node c1.


Notes:

If the two linked lists have no intersection at all, return null.
The linked lists must retain their original structure after the function returns.
You may assume there are no cycles anywhere in the entire linked structure.
Your code should preferably run in O(n) time and use only O(1) memory.
</pre>
# My Code:
<pre>
	class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if(!headA || !headB)return NULL;
        ListNode* pa = headA;
        ListNode* pb = headB;
        while(pa && pb && pa != pb){
            pa=pa -> next;
            pb=pb -> next;
            if(pa == pb)return pa;
            if(pa == NULL)pa = headB;
            if(pb == NULL)pb = headA;
        }
        return pa;
    }
};
</pre>
#思路：
<pre>
	如果用暴力法来解的话时间复杂度是O(m*n)，会TLE；这里如果画下图的话能够比较明显的找到另一种比较好的方法。这两条链表有一个特性就是相交节点后面的“长度”是一样的，所以我们想象一下将两条链表排成如图所示的样子，当pa走完链表A时再到链表B走（pb也是如此），那么找到这个相交节点的时间复杂度就是O(m+n)了。   同时如果两条链表没有交点，那么就达到最坏的情况了，也就是pa和pb分别同时走到链表B和链表A的末尾，也就是值为NULL的节点，那么这时候pa==pb，返回了pa，即NULL。
</pre>

<img src="http://www.nkuhjp.top/images/%E5%8F%8C%E9%93%BE%E8%A1%A8.png" alt="">
