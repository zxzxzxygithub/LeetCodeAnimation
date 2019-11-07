链接：https://github.com/MisterBooo/LeetCodeAnimation/blob/master/notes/LeetCode%E7%AC%AC1%E5%8F%B7%E9%97%AE%E9%A2%98%EF%BC%9A%E4%B8%A4%E6%95%B0%E4%B9%8B%E5%92%8C.md
算法和注释：
class Solution{
    public:
        
        /**
         *
         *@param nums  数组
         *@param target 目标和
         */
        vector<int> twoSum(vector<int>& nums, int target){
            // 1. 定义无序的map变量record，key，value均为int
            //    其中key为nums中的数字，value为nums中的下标index
            unordered_map<int,int> record;
            // 2. 对数组nums进行遍历
            for(int i = 0; i < nums.size(); i++){
                // 3. 求目标值与当前数值的差，设为complement
                int complement = target - nums[i];
                // 4. 如果从map中查找到了这个值
                if(record.find(complement) != record.end()){
                // 4.1 新建数组，把这个值的下标和表中的值的下标存进来    
                    int res[] = {i, record[complement];}
                // 4.2 返回一个vector      
                    return vector<int>(res, res + 2);
                }
                // 4.3 没有找到这个值则把nums中的这个值和索引存入record 
                record[nums[i]] = i;
            }
        }
}
