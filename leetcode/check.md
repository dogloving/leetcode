```cpp
class Solution {
public:
    int countArrangement(int N) {
    	vector<int> nums;
    	nums.push_back(0);
    	for(int i = 1;i <= N;++i)
    	    nums.push_back(i);
    	return helper(N,nums);
    }
private:
    int helper(int n,vector<int>& nums){
        if(n <= 1)return 1;
        int result = 0;
        for(int i = 1;i <= n;++i){
            if(nums[i]%n == 0 || n%nums[i] == 0){
                swap(nums[i],nums[n]);
                result += helper(n-1,nums);
                swap(nums[i],nums[n]);
            }
        }
        return result;
    }
};
```


<pre></pre>
