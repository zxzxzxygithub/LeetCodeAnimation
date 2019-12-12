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



