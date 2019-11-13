https://leetcode-cn.com/problems/valid-parentheses/

给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

示例 1:

输入: "()"
输出: true

示例 3:

输入: "(]"
输出: false

```
class Solution{
    // 声明hashmap变量mappings
    private HashMap<Character, Character> mappings;
    // 
    public solution(){
        // 1.初始化mappings变量
        this.mappings = new HashMap<Character,Character>();
        // 2.mappings分别put进去三组括号，开括号为key，闭括号为value
        this.mappings.put(')','(');
        this.mappings.put('}','{');
        this.mappings.put(']','[');
    }

    /**
    *@param s 输入的字符串
    */
    public boolean isValid(String s){

        // 1. 初始化一个栈
        Stack<Character> stack = new Stack<Character>();
        // 2. 遍历s的每个字符
        for(int i = 0; i < s.length(); i ++){
            // 2.1 获取i位置的字符
            char c = s.charAt(i);
            // 2.2 查看mappings中是否包含这个key，当包含的时候的处理如下
            if(this.mappings.containsKey(c)){
                // 2.3 判断栈是否为空，如果不为空则获取最顶端元素
                char topElement = stack.empty() ? '#' :stack.pop(); 
                // 2.4 如果栈顶元素和当前元素相互不为一对括号，返回false
                if(topElement != this.mappings.get(c)){
                    return false;
                }
            }else{
                // 2.5
                stash.push(c);
            }   
        }
        // 2.6 判断栈是否为空，如果不为空则说明没有匹配完，是非法的
        return stack.isEmpty();

    }
}
```
