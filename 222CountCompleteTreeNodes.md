# Problem Describe:
<pre>
	Given a complete binary tree, count the number of nodes.

Definition of a complete binary tree from Wikipedia:
In a complete binary tree every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.
</pre>

# My Code
<pre>
	/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int countNodes(TreeNode* root) {
        TreeNode *left = root,*right = root;
        int hLeft = 0,hRight = 0;
        while(left && ++hLeft)left = left->left;
        while(right && ++hRight)right = right->right;
        if(hLeft == hRight)return pow(2,hLeft)-1;
        return countNodes(root->left)+countNodes(root->right)+1;
    }
};
</pre>

# 思路
一开始想到的是将整棵树遍历一遍，时间复杂度O(n)，竟然时间超限。然后利用它是完全二叉树的条件，如果分别沿着最左和最右往下高度刚好一样，那么节点总数就可以求出来了。时间复杂度O(lgn ^2)
