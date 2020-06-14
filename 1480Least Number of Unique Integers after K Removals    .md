```CPP
class Solution {
public:
    int findLeastNumOfUniqueInts(vector<int>& arr, int k) {
        unordered_map<int,int> num_cnt;
        for (int n: arr) num_cnt[n]++;
        vector<int> cnts;
        for (auto it: num_cnt) cnts.push_back(it.second);
        sort(cnts.begin(), cnts.end());
        int res = cnts.size();
        for (int cnt: cnts) {
            if (k>cnt) {
                k -= cnt;
                --res;
            } else if (k==cnt) {
                --res;
                break;
            } else break;
        }
        return res;
    }
};
```

