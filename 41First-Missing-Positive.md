# Problem Describe:
Given an unsorted integer array, find the first missing positive integer.
# My Code:
<pre>
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
    int size=nums.size();
    if(size==0)return 1;
    vector<int> num;
    for(int i=0;i<=size;i++)
        num.push_back(0);
    for(int i=0;i<size;i++)
        if(nums[i]>0 && nums[i]<=size){
            num[nums[i]]=1;
        }
    int flag=size+1;
    for(int i=1;i<=size;i++)
        if(num[i]==0){
            flag=i;break;
        }
    return flag;
    }
};
</pre>
# 思路
这题要找的是第一个缺失的正整数。所以我先定义一个和原数组nums同等大小的数组num，将里面的元素初始化为0；然后遍历原数组，如果num[i]为整数并且小于等于nums.size()，就使num[nums[i]]=1，表示这个数出现过。最后遍历num，如果num[i]为0，则说明i这个数没有出现过，如果num[i]全部等于0，说明size+1没有出现过。时间复杂度O(n)。
