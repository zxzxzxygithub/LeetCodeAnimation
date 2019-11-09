链接： https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/

示例：
给定一个字符串，找出不含有重复字符的最长子串的长度。

示例 1:  
输入: "abcabcbb"  
输出: 3  
解释: 无重复字符的最长子串是 "abc"，其长度为 3。

示例 2:  
输入: "bbbbb"  
输出: 1.    
解释: 无重复字符的最长子串是 "b"，其长度为 1。

示例 3:    
输入: "pwwkew"  
输出: 3  
解释: 无重复字符的最长子串是 "wke"，其长度为 3。    
请注意，答案必须是一个子串，"pwke" 是一个子序列 而不是子串。

代码：
```
public class Solution]{


    /**判断给定字符串中无重复字符的最长子串*/
    public int lengthOfLongestSubstring(String s){
        // 1. 给定变量n，将s的长度赋值给他
        int n = s.length();
        // 2. 初始化变量ans为0
        int ans = 0;
        // 3. 遍历这个给定字符串
        for(int i=0; i<n;i++){
            // 3.1 从给定字母的下一个字母开始遍历给定的字符串
            for(int j=i+1;j<n;j++){
                // 3.2 如果这个字串没有重复的
                if(allUnique(s,i,j)){
                    // 3.3 取ans和j-i的差值中的最大值赋值给ans
                    ans = Math.max(ans, j-1);
                }
            }    
        }
        return ans;

    }
    
    /**给定一个字符串，以及他的开始和结束下标，判断这两个下标之间的字串是否有重复的字母*/
    public boolean allUnique(String s, int start, int end){
        // 1.初始化一个set（set具有去重的作用）
        Set<Character> set = new HashSet<>();
        // 2.遍历指定下标的字串
        for(int i = start; i < end; i++){
            // 2.1 依次取出该子串中的字母
            Character ch = s.charAt(i);
            // 2.2 判断set中是否已存在这个串，如果存在则返回false
            if(set.contains(ch)){
                return false;
            }
            // 2.3 如果不存在则加入set
            set.add(ch);
        }
        return true;

    }
}
```
