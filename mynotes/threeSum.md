https://leetcode-cn.com/problems/3sum/


给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。

例如, 给定数组 nums = [-1, 0, 1, 2, -1, -4]，



满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]


代码

```
var threeSum = function(nums){
    // 最左侧值为定值，右侧所有值进行两边推进计算
    // 1. 初始化一个数组res
    let res = [];
    // 2. 对输入数组按大小进行排序（预处理）
    nums.sort((a,b)=> a - b);
    // 3. 求出输入数组的长度
    let size = nums.length;
    // 4. 如果第一个数小于等于0，最后一个数大于等于0才有解
    if(nums[0] <= 0 && nums[size - 1] >= 0){
        // 5. 设置变量i为0
        let i = 0;
        // 6. 进行循环,i为倒数第三个的时候结束循环
        while(i < size -2){
            // 6.1.条件判断：最左侧大于0，无解
            if(nums[i] >0)break;
            // 6.2 i后面的下标赋值给first
            let first = i + 1;
            // 6.3 最后一个元素赋值给last
            let last = size -1;
            // 6.4 first小于last的时候进行循环
            while(first < last){
                // 6.4.1  三数同号，无解
                if(nums[i] * nums[last] > 0){
                    break;
                }
                // 6.4.2 三数相加
                let sum = nums[i] + nums[first] + nums[last];
                // 6.4.3 判断是否满足三数之和等于0，满足则记录下这几个数
                if(sum == 0){
                    res.push(nums[i], nums[fist], nums[last]);
                }
                // 6.4.4 负数过小，first右移
                if(sum <= 0){
                    // 6.4.5 重复值跳过
                    while(nums[first] === nums[++first]){}
                }else{
                    // 6.4.6 正数过大，last左移,重复值跳过
                    while(nums[last] === nums[--last]){}
                    }
            }
            // 6.5 i右移，重复值跳过
            while(nums[i] === nums[++i]）{}
        }
    }
    return res;

}
```


