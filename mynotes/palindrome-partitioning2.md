https://leetcode-cn.com/problems/palindrome-partitioning/solution/xiang-xi-tong-su-de-si-lu-fen-xi-duo-jie-fa-by-3-7/

解法二 分治优化

**为了避免一些重复判断，可以用动态规划的方法，把所有字符是否是回文串提前存起来。**

对于字符串 s
用dp[i][j] 表示s[i,j]是否是回文串
然后有 dp[i][j] = s[i] == s[j] && dp[i+1][j-1]

我们只需要两层 for 循环，从每个下标开始，考虑所有长度的子串即可。

boolean[][] dp = new boolean[s.length()][s.length()];
int length = s.length();
// 考虑所有长度的子串
for(int len =1; len <= length; len++){
    // 从每个下表开始
    for(int i = 0; i <= s.length - len; i++){
        int j = i + len -1;
        dp[i][j] = s.charAt(i) == s.charAt(j) && (len < 3 || dp[i + 1][j - 1]);
    }
}
因为要保证dp[i + 1][j - 1] 中 i + 1 < = j -1
i + 1 < = j -1
把j = i + len - 1 代入上式
i + 1 <= i + len - 1 - 1
化简得
len >= 3
所以为了保证正确，多加了 len < 3 的条件。也就意味着长度是 1 和 2 的时候，我们只需要判断 s[i] == s[j]。
然后把 dp 传入到递归函数中即可

public List<List<String>> partition(String s){
    boolean[][] dp = new boolean[s.length()][s.length()];
    int length = s.length();
    for(int len = 1;len <= length; len++){
        for(int i = 0; i <= s.length()-len; len++){
            int j = i + len -1;
            dpp[i][j] = s.charAt(i) == s.charAt(j) && (len < 3 || dp[i+1][j-1]);                                                                                                                                                                                                                                                                                                                                                                                           
        }
    }
    return partitionHelper(s,0,dp);
}

private List<List<String>> partitionHelper(String s, int stat, boolean[][] dp){

    if(start == s.length){
        List<String> list = new ArrayList<>();
        List<List<String>> ans= new ArrayList<>();
        ans.add(list);
        return ans;
    }

    List<List<String>> ans = new ArrayList<>();
    for(int  i = start; i < s.length(); i++){
        if(dp[start][i]){
            String left = s.substring(start, i+1);
            for(List<String> l: partitionHelper(s, i+1, dp)){
                l.add(0,left);
                ans.add(l);
            }
        }
    }

    return ans;
}

