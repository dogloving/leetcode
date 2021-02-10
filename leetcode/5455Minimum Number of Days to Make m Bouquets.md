```CPP
class Solution {
public:
    int minDays(vector<int>& bloomDay, int m, int k) {
        int n = bloomDay.size();
        if (m*k>n) return -1;
        vector<int> copy = bloomDay;
        sort(copy.begin(), copy.end());
        int left = 0, right = n-1;
        int res = INT_MAX;
        while (left!=right) {
            int mid = left+(right-left)/2;
            int MAX = copy[mid];
            int f = 0, b = 0;
            for (int x: bloomDay) {
                if (x<=MAX) {
                    ++f;
                    if (f==k) {
                        ++b;
                        f = 0;
                    }
                } else f = 0;
                if (b==m) {
                    res = min(res, MAX);
                    right = mid;
                    break;
                }
            }
            if (right!=mid) left = mid+1;
        }
        int MAX = copy[left];
        int f = 0, b = 0;
        for (int x: bloomDay) {
            if (x<=MAX) {
                ++f;
                if (f==k) {
                    ++b;
                    f = 0;
                }
            } else f = 0;
            if (b==m) {
                res = min(res, MAX);
                break;
            }
        }
        return res;
    }
};
```

思路：二分法，然后检查copy[mid]是否可行。