# Problem Describe:
<pre>
	Given an array of n positive integers and a positive integer s, find the minimal length of a subarray of which the sum ≥ s. If there isn't one, return 0 instead.

	For example, given the array [2,3,1,2,4,3] and s = 7,
	the subarray [4,3] has the minimal length under the problem constraint.

	click to show more practice.

	More practice:
	If you have figured out the O(n) solution, try coding another solution of which the time complexity is O(n log n).
</pre>
# My Code:
<pre>
	class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        if(nums.size()==0)
            return 0;
        int start=0,end=0;
        int min=1;
        int minLength=9999999;
        int sum=nums[0];
        while(end!=nums.size()){
            if(sum>=s){
            	minLength=minLength<min?minLength:min;
                sum-=nums[start];
                start++;
                min=end-start+1;
            }
            else if(sum<s){
                end++;
                sum+=nums[end];
                min=end-start+1;
            }
        }
        if(end-start==nums.size() && sum<s)
            return 0;
        return minLength;
    }
};
</pre>
# 思路：
这题主要思路是设置start和end两个“指针”，从左往右走；如果和sum大于s就先将此时的end-start+1和当前minLength比较然后更新minLength和sum，然后start++;如果和小于s就end++，更新sum。
