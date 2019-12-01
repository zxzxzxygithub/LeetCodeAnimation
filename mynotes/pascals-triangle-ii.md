https://leetcode-cn.com/problems/pascals-triangle-ii/

给定一个非负索引 k，其中 k ≤ 33，返回杨辉三角的第 k 行。

在杨辉三角中，每个数是它左上方和右上方的数的和。
示例:

输入: 3
输出: [1,3,3,1]

```
class Solution{
public:
    vector<int> getRow(const int rowIndex){
        vector<int> ans;
        for(int i = 0; i <= rowIndex; ++i)
            ans.push_back(combination(rowIndex,i));
        return ans    
    }
private:
    int combination(const int m, const int i){
        long long n = min(i, m - i);
        long long k = m - n;
        long long c = 1;
        for(long long j = 1; j <= n; ==j){
            c *=(k + j);
            c /=j;
        }
        return c;
    }        
}

```
