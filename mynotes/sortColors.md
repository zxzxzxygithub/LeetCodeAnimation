https://leetcode-cn.com/problems/sort-colors/

给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

注意:
不能使用代码库中的排序函数来解决这道题。

示例:

输入: [2,0,2,1,1,0]
输出: [0,0,1,1,2,2]

代码：

```
class Solution{
    /***
    *
    *@param nums 给定的数组包含0，1，2
    /
    public void sortColors(int[] nums){
        // 1. 初始化两个变量p0，和cur，p0为0值所在下标的指针，cur为当前指针
        int p0 = 0,cur = 0;
        // 2. 初始化变量p2，为2值的下标指针
        int p2 = nums.length - 1;
        // 3. 初始化一个变量tmp
        int tmp;
        // 4. 循环，当cur右移到p2的时候结束循环
        while(cur <= p2){
            // 4.1 当当前元素为0时，
            if(nums[curr] == 0){
                // 4.2 p0元素值赋值给tmp
                tmp = nums[p0];
                // 4.3 当前元素值赋值给p0指向的元素，p0向右移动一位
                nums[p0++] = nums[curr];
                // 4.4 p0的值复制给curr指针，同时curr右移一位
                nums[curr++] = tmp;
            }else if(nums[curr] == 2){
                // 4.5 当前元素值为2的时候
                // 4.6 当前元素值赋值给tmp
                tmp = nums[curr];
                // 4.7 p2指向的元素值赋值给当前位置的元素值
                nums[curr] = nums[p2];
                // 4.8 tmp赋值给p2所在的值，并将p2向左移一位
                nums[p2--] = tmp  
            }else{
                curr ++;
            }
        }
    }
}
```
