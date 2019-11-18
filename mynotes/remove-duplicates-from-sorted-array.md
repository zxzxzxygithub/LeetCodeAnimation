https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/

给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

示例 2:
               1        
给定 nums = [0, 0, 2, 3, 4, 2, 2, 3, 3, 4],
                        i                 
                                        j 

函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。

你不需要考虑数组中超出新长度后面的元素。

代码：

```
/**
*
*@param nums 给定的数组
*/
public int removeDuplicates(int[] nums){
    // 0. 排除特殊情况：空数组直接返回长度0
    if(nums.length == 0){ return 0}
    // 1. 初始化变量i
    int i = 0;
    // 2. 从下标1开始循环数组
    for(int j = 1; j < nums.length; j++){
        // 2.1 后一个元素和前一个元素不相同的时候
        if(nums[j] != nums[i]){
            // 2.2 不相同则i右移一位，并把当前j下标对应的值赋给i小标位置
            i ++；
            nums[i] = nums[j]
        }
    }
    // 3 返回新数组的长度
    return i+1;
}

```

