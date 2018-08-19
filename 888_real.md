```CPP
class Solution {
public:
    vector<int> fairCandySwap(vector<int>& A, vector<int>& B) {
        int sum_a = accumulate(A.begin(), A.end(), 0),
            sum_b = accumulate(B.begin(), B.end(), 0);
        int ave = (sum_a + sum_b) / 2;
        vector<int> res;
        unordered_set<int> set_a = unordered_set<int>(A.begin(), A.end()),
            set_b = unordered_set<int>(B.begin(), B.end());
        for (int num_a: set_a) {
            int target = ave + num_a - sum_a;
            if (set_b.count(target)) {
                res = {num_a, target};
                break;
            }
        }
        return res;
    }
};
```
<pre>
题意是:
A和B各有一些bar的糖果，现在A给B一个bar的糖果，B给A一个bar的糖果，使得二者糖果数一样多。

思路如下：
先将两个数组各自的和求出来，然后求出平均数ave，就是最终A和B要成为的数。我们遍历A中每个数num_a，如果把num_a给B，
那么我们需要B给A (ave + num_a - sum_a)这么多的数，如果B中刚好有说明可以这样交换。
最后的时间复杂度为O(NlogN)，空间复杂度为O(N)。
</pre>
