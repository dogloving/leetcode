# Problem Describe:
<pre>
Given two numbers represented as strings, return multiplication of the numbers as a string.

Note:
The numbers can be arbitrarily large and are non-negative.
Converting the input string to integer is NOT allowed.
You should NOT use internal library such as BigInteger.
</pre>
# My Code:
<pre>
	string multiply(string num1, string num2) {
	vector<int> num11, num22;
	vector<vector<int>> ret;
	for (int i = 0; i<num1.size(); i++)num11.push_back(num1[i] - '0');
	for (int i = 0; i<num2.size(); i++)num22.push_back(num2[i] - '0');
	for (int i = num11.size() - 1; i >= 0; i--)
	{
		vector<int> temp;
		for (int j = 0; j<num11.size() - 1 - i; j++)temp.push_back(0);
		for (int j = num22.size() - 1; j >= 0; j--)temp.push_back(num11[i] * num22[j]);
		temp.push_back(0);
		for (int j = 0; j<temp.size(); j++)
		{
			if (temp[j] >= 10)
			{
				temp[j + 1] += temp[j] / 10;
				temp[j] %= 10;
			}
		}
		ret.push_back(temp);
	}
	vector<int> result;
	for (int j = 0; j<num1.size() + num2.size() + 1; j++)
	{
		int sum = 0;
		for (int i = 0; i<num11.size(); i++)
		{
			if (j>ret[i].size() - 1)continue;
			else sum += ret[i][j];
		}
		result.push_back(sum);
	}
	for (int i = 0; i<result.size(); i++)
	{
		if (result[i] >= 10)
		{
			result[i + 1] += result[i] / 10;
			result[i] %= 10;
		}
	}
	string s = "";
	bool flag = false;
	for (int i = result.size() - 1; i >= 0; i--)
	{
		if (!flag && result[i] != 0)
		{
			s += result[i] + '0';
			flag = true;
		}
		else if (flag)
			s += result[i] + '0';
	}
	if (s == "")s = "0";
	return s;
}
</pre>
# 思路:
这题是大数相乘。其实不难，不过过程有点烦。我的做法是先用一维数组储存num11的某位与num22的乘积，为了不超出范围，我用一个元素储存个位与个位的积。然后用一个二维数组可以储存下结果，最后只要加一下进个位什么的就行了。
