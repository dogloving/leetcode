```CPP
class Solution {
public:
    bool repeatedSubstringPattern(string s) {
        int len = s.size();
        if (len<2) return false; 
        for (int l = len-1; l >= 1; --l) {
            if (len%l==0) {
                bool ok = true;
                for (int idx_start = l; idx_start<len; idx_start+=l) {
                    for (int i1=0,i2=idx_start; i1<l; ++i1,++i2) {
                        if (s[i1]!=s[i2]) {
                            ok = false;
                            break;
                        }
                    }
                    if (!ok) break;
                }
                if (ok) return true;
            }
        }
        return false;
    }
};
```

题意：非空字符串，检查该字符串是否能由重复子串拼接而成。

思路：