# Problem Describe:
<pre>
Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

For example,
Given the following matrix:

[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
You should return [1,2,3,6,9,8,7,4,5].
</pre>
# My Code:
<pre>
class Solution {
public:
	vector<int> spiralOrder(vector<vector<int>>& matrix) {
	vector<int> result;
	if (matrix.size() == 0)
		return result;
	int m, n;
	m = matrix[0].size();
	n = matrix.size();
	int count = 0;
	int i = 0, j = 0;
	while (count != m*n) {
		while (count != m*n && j != m && matrix[i][j] != -10086) {
			result.push_back(matrix[i][j]);
			matrix[i][j] = -10086;
			count++;
			j++;
		}
		j--;
		i++;
		while (count != m*n && i != n && matrix[i][j] != -10086) {
			result.push_back(matrix[i][j]);
			matrix[i][j] = -10086;
			count++;
			i++;
		}
		i--;
		j--;
		while (count != m*n && j != -1 && matrix[i][j] != -10086) {
			result.push_back(matrix[i][j]);
			matrix[i][j] = -10086;
			count++;
			j--;
		}
		j++;
		i--;
		while (count != m*n && i != -1 && matrix[i][j] != -10086) {
			result.push_back(matrix[i][j]);
			matrix[i][j] = -10086;
			count++;
			i--;
		}
		i++;
		j++;
	}
	return result;
}
};
</pre> 
# 思路：
注意几个点：  1.一开始我把走过的点改成了-1，但是测试数据中有-1，然后改成了-10086这种奇怪的数（嘿嘿）；2.注意每次走完一个while循环后要先往前走一个单位，不然如果还是在刚才走的最后一个位置就会因为该位置值是-10086而一直不能进入后续循环，从而使得时间超限，这就是为什么我会在每个while循环后加上i++j--之类的原因；3.注意四个while循环不能更换顺序，因为这是右下左上的顺序，而每次都是重复这种顺序；