# Problem Describe:
<pre>
	Given an array of strings, group anagrams together.

For example, given: ["eat", "tea", "tan", "ate", "nat", "bat"], 
Return:

[
  ["ate", "eat","tea"],
  ["nat","tan"],
  ["bat"]
]
Note: All inputs will be in lower-case.
</pre>
# My Code:
<pre>
	class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> result;
        map<string,int> mp;
        int dictSize=0;
        for(int i=0;i<strs.size();++i){
            string tmp=strs[i];
            sort(tmp.begin(),tmp.end());
            if(mp.count(tmp)){
                result[mp[tmp]].push_back(strs[i]);
            }
            else{
                result.push_back(vector<string>{strs[i]});
                mp[tmp]=dictSize++;
            }
        }
        return result;
    }
};
</pre>
# 思路：
肯定是要对每个string对象进行重新排序（或者其他方法），这样才能方便对比。所以我的思路是构造一个字典，每次判断一个字符串之前是否有出现过就在字典中查找，如果有查到就直接添加到之前的容器中，否则新创建一个容器用来存放同一类的字符串，然后往字典中添加这个字符串。
