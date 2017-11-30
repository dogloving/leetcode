```CPP
class MyCalendarThree {
public:
    MyCalendarThree() {
        unordered_map<pair<int, int>, int> seg_count;
    }
    
    int book(int start, int end) {
        int max_count = 0;
        for (auto it = seg_count.begin(); it != seg_count.end(); ++it) {
            auto pr = it->first;
            auto cnt = it->second;
            int st = pr.first, ed = pr.second;
            max_count = max(cnt, max_count);
            if ((start >= st && start < ed) || (st >= start && st < end)) {
                auto four_node = sort_four({start, st, end, ed});
                if (four_node[0] != four_node[1]) {
                    if (four_node[0] == st)
                        seg_count[make_pair(four_node[0], four_node[1])] = cnt;
                    else
                        seg_count[make_pair(four_node[0], four_node[1])] = 1;
                }
                if (four_node[1] != four_node[2]) {
                    seg_count[make_pair(four_node[1], four_node[2])] = cnt + 1;
                }
                if (four_node[2] != four_node[3]) {
                    if (four_node[2] == st)
                        seg_count[make_pair(four_node[2], four_node[3])] = cnt;
                    else
                        seg_count[make_pair(four_node[2], four_node[3])] = 1;
                }
                max_count = max(max_count, cnt + 1);
            }
        }
        if (max_count == 0) {
            seg_count[make_pair(start, end)] = 1;
        }
        return max(1, max_count);
    }
private:
    vector<int> sort_four(vector<int> raw) {
        sort(res.begin(), res.end());
        return res;
    }
};

/**
 * Your MyCalendarThree object will be instantiated and called as such:
 * MyCalendarThree obj = new MyCalendarThree();
 * int param_1 = obj.book(start,end);
 */
 ```
