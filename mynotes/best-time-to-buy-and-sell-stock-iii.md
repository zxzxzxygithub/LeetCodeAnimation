https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-iii/

给定一个数组，它的第 i 个元素是一支给定的股票在第 i 天的价格。

设计一个算法来计算你所能获取的最大利润。你最多可以完成 两笔 交易。

注意: 你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。

示例 1:

输入: [3,3,5,0,0,3,1,4]
输出: 6
解释: 在第 4 天（股票价格 = 0）的时候买入，在第 6 天（股票价格 = 3）的时候卖出，这笔交易所能获得利润 = 3-0 = 3 。
     随后，在第 7 天（股票价格 = 1）的时候买入，在第 8 天 （股票价格 = 4）的时候卖出，这笔交易所能获得利润 = 4-1 = 3 。

示例 2:
输入: [1,2,3,4,5]
输出: 4
解释: 在第 1 天（股票价格 = 1）的时候买入，在第 5 天 （股票价格 = 5）的时候卖出, 这笔交易所能获得利润 = 5-1 = 4 。   
     注意你不能在第 1 天和第 2 天接连购买股票，之后再将它们卖出。   
     因为这样属于同时参与了多笔交易，你必须在再次购买前出售掉之前的股票。

示例 3:
输入: [7,6,4,3,1] 
输出: 0 
解释: 在这个情况下, 没有交易完成, 所以最大利润为 0。

```
#「状态」穷举
for 状态1 in 状态1的所有取值:
    for 状态2 in 状态2的所有取值：
        for 状态3 in 状态3的所有取值：
            ...
            dp[状态1][状态2][...] = 择优(选择1，选择2，选择3...)

# 买卖股票的三种状态 买入，卖出，无操作，用buy，sell，rest来选择
# 限制：sell必须在buy之后，buy必须在sell之后
# rest的两种状态：buy之后的rest，sell之后的rest
# 次数限制buy只能在k>0的情况下操作，buy一次，k减一

#本题有三个状态：1.天数 2.允许交易的最大次数 3.持有状态（1.持有，2.没有持有）
dp[i][k][0 or 1]
0 <= i <= n - 1 #n为天数
1 <= k <= K #K为最多交易次数
#此问题共有n*k*2种状态，全部穷举就能搞定
for 0 <= i < n:
    for 1 <= k <= K:
        for s in {0,1}:
            dp[i][j][s] = max(buy, sell, rest)
#用自然语言描述出每一个状态的含义
dp[3][2][1]:第三天，2次交易，持有股票   
dp[2][3][0]：第二天，3次交易，没有持有股票
#寻求的最终答案：dp[n - 1][K][0]：最后一天，交易了k次，股票已卖出，即不持有股票
# 状态转移框架
dp[i][k][0] = max(dp[i-1][k][0],dp[i-1][k][1]+prices[i])
            = max(选择rest      ，选择sell)
 解释：今天我没有持有股票，有两种可能：
 要么是我昨天就没有持有，然后今天选择rest，所以我今天还是没有持有；
 要么是我昨天持有股票，但是今天我sell了，所以我今天没有持有股票了。

 dp[i][k][1] = max(dp[i-1][k][1], dp[i-1][k-1][0]-prices[i])
             = max(选择rest，      选择buy)
 解释：今天我持有股票，有两种可能： 
 要么昨天我就持有股票，然后今天选择rest，所以我今天还持有着股票，
 要么我昨天没有持有，但今天我选择buy，所以今天我就持有股票了   

 # 定义base case，即最简单的情况
 dp[-1][k][0] = dp[i][0][0] = 0
 dp[-1][k][1] = dp[i][0][1] = - infinity

 # 状态转移方程：
 dp[i][k][0] = max(dp[i-1][k][0],dp[i-1][k][1]+prices[i])
 dp[i][k][1] = max(dp[i-1][k][1],dp[i-1][k-1][0]-prices[i])  

第一题，k = 1
for(int i = 0; i < n; i++){
    // i = 0边界情况
    if(i-1=-1){
        dp[i][0] = 0;
        dp[i][1]=-prices[i];
        continue;
    }
    dp[i][0] =  Math.max(dp[i-1][0],dp[i-1][1] + prices[i]);
    dp[i][1] =  Math.max(dp[i-1][1], -prices[i]);
}
return dp[n-1][0]

```
