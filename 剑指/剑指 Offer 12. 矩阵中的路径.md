```cpp
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        if (board.empty() || board[0].empty()) 
            return word.empty();
        for (int row = 0; row < board.size(); ++row) {
            for (int col = 0; col < board[0].size(); ++col) {
                if (backtrack(board, row, col, word, 0)) return true;
            }
        }
        
        return false;
    }
private:
    bool backtrack(vector<vector<char>> &board, int row, int col, 
                   const string &word, int idx) {
        if (idx == word.size()) return true;
        if (row < 0 || row >= board.size() || 
            col < 0 || col >= board[0].size()) return false;
        if (word[idx] != board[row][col]) return false;
        
        board[row][col] = '*';
        if (backtrack(board, row - 1, col, word, idx + 1) || 
            backtrack(board, row + 1, col, word, idx + 1) ||
            backtrack(board, row, col - 1, word, idx + 1) || 
            backtrack(board, row, col + 1, word, idx + 1)) 
            return true;
        
        board[row][col] = word[idx];
        return false;
    }
};
```

