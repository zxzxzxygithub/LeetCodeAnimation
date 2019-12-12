https://leetcode-cn.com/problems/palindrome-partitioning/

给定一个字符串 s，将 s 分割成一些子串，使每个子串都是回文串。

返回 s 所有可能的分割方案。

示例:

输入: "aab"
输出:
[
  ["aa","b"],
  ["a","a","b"]
]

解法一 分治

这道题的话，举个例子。

aabb
先考虑在第一个位置切割，a | abb，
这样我们只需要知道abb的所有结果，然后在所有结果的头部把a加入，
abb的所有结果就是【a b b】[a bb]
每个结果头部加入a，就是[a a b b][a a bb]

aabb
再考虑第2个位置切割 ，aa | bb
这样我们只需要知道bb的所有结果，然后在所有结果的头部把aa加入，
 bb的所有结果就是[b b][bb]
 每个结果头部加入aa就是，[aa b b] [aa bb]


aabb
再考虑在第三个位置切割， aab | b
因为aab不是回文串，所以直接跳过

aabb
再考虑在第四个位置切割， aabb
因为aabb不是回文串，所以直接跳过

最后所有的结果就是所有的加起来
[a a b b ][a a bb][aa b b][aa bb]

然后中间的过程求 abb的所有结果，求abb的所有结果等等，就可以递归的去求，递归出口的话，就是空串的所有子串
就是一个空的 list 即可。

```
public List<List<String>> partition(String s){
    return partitionHelper(s, 0);
}

private List<List<String>> partitionHelper(String s, int start){
    // 递归出口，空字符串
    if(start == s.length){
        List<String> list = new ArrayList<>();
        List<List<String>> ans = new ArrayList<>();
        ans.add(list);
        return ans;
    }
    List<List<String>> ans = new ArrayList<>();
    for(int i = stat; i < s.length(); i++){
        // 当前切割后是回文串才考虑
        if(isPalindrome(s.subString(start, i+1))){
            String left = s.subString(start, i+1);
            // 遍历后面字符串的所有结果，将当前的字符串加到头部
            for(List<String> l : partitionHelper(s, i+1)){
                l.add(0,left);
                ans.add(l);
            }

        }
    }

    return ans;

}

private boolean isPalindrome(String s){
    int i = 0;
    int j = s.length() -1;
    while(i < j ){
        if(s.charAt(i) != s.charAt(j)){
            return false;
        }
        i++;
        j++;
    }
    return true;
}

```
