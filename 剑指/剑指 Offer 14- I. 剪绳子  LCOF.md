```cpp
class Solution {
public:
    int cuttingRope(int n) {
        int res = 0;
        vector<vector<int>> dp(n+1,vector<int>(n+1,1));
        for (int k = 0; k <= n; k++) dp[0][k] = 0;
        for (int l = 0; l <= n; l++) dp[l][1] = l;
        for (int l = 1; l <= n; l++) {
            for (int k = 2; k <= l; k++) {
                for (int sl = 1; sl<=l&&(l-sl>=k-1); sl++) {
                    dp[l][k] = max(dp[l][k],dp[l-sl][k-1]*sl);
                    res = max(res,dp[l][k]);
                }
            }
        }
        return res;
    }
};
```

思路：令dp[l][k]表示长度为l分成k段的最大乘积。