```CPP
class Solution {
public:
    int binaryGap(int N) {
        int res = 0;
        int last = -1, cnt = 0;
        while (N) {
            int mod = N & 1;
            if (mod) {
                if (last != -1) res = max(res, cnt - last);
                last = cnt;
            }
            N >>= 1;
            ++cnt;
        }
        return res;
    }
};
```
