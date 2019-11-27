
https://leetcode-cn.com/problems/binary-tree-level-order-traversal/


给定一个二叉树，返回其按层次遍历的节点值。 （即逐层地，从左到右访问所有节点）。

例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7

返回其层次遍历结果：

[
  [3],
  [9,20],
  [15,7]
]

代码：

```
class Solution{
 
   // 1. 全局变量，用来存储最终的结果 
    List<List<Integer>> levels = new ArrayList<List<Integer>>();

   // 2.递归方法，用于传入node，level获取当前level的list
    public void helper(TreeNode node, int level){
     // 3.level和levels的size对应，相等则新建list
     if(levels.size() == level){
         levels.add(new ArrayList<Integer>());
     }

     // 4. 把节点的值加入list
     levels.get(level).add(node.val);

     // 5. 递归左节点
     if(node.left != null){
         helper(node.left, level + 1);
     }

     // 6. 递归右节点
     if(node.right != null){
         helper(node.right, level + 1);
     }    

    }

    // 7.递归求列表集合
    public List<List<Integer>> levelOrder(TreeNode root){
    
       if(root == null)return levels;

       helper(root, 0);

       return levels;
    }

}

```

