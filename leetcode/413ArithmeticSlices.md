# Problem Describe:
<pre>
	A sequence of number is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.

For example, these are arithmetic sequence:

1, 3, 5, 7, 9
7, 7, 7, 7
3, -1, -5, -9
The following sequence is not arithmetic.

1, 1, 2, 5, 7

A zero-indexed array A consisting of N numbers is given. A slice of that array is any pair of integers (P, Q) such that 0 <= P < Q < N.

A slice (P, Q) of array A is called arithmetic if the sequence:
A[P], A[p + 1], ..., A[Q - 1], A[Q] is arithmetic. In particular, this means that P + 1 < Q.

The function should return the number of arithmetic slices in the array A.
</pre>

# My Code
<pre>
	class Solution {
public:
    int numberOfArithmeticSlices(vector<int>& A) {
        vector<int> cha;
        for(int i=1;i<A.size();++i)
            cha.push_back(A[i]-A[i-1]); 
        vector<int> lianxu;
        int start=0;
        for(int i=1;i<cha.size();++i){
            if(cha[i]!=cha[i-1] && i-start>=2){
                lianxu.push_back(i-start);
                start=i;
            }
            else if(cha[i]!=cha[i-1] && i-start<2)
                ++start;
            if(i==cha.size()-1 && cha[i]==cha[i-1])
                lianxu.push_back(i-start+1);
        }
        int count=0;
        for(auto i:lianxu){
            int sum=0;
            for(int j=1;j<=i-1;++j)
                sum+=j;
            count+=sum;
        }
        return count;
    }
};
</pre>

# 思路
先将每两个相邻的数的差保存在数组cha中，然后遍历这些差，记录下连续的差的个数（仅将连续数量大于等于2的保存在数组lianxu中），因为对于n个差连续，最多可以有1+2+…+(n-1)个slice，所以将数组lianxu中每种求出来相加就行。
