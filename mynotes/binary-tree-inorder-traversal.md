https://leetcode-cn.com/problems/binary-tree-inorder-traversal/

给定一个二叉树，返回它的中序 遍历。

示例:
输入: [1,null,2,3]
   1
    \
     2
    /
   3

输出: [1,3,2]

代码：

```
class Solution{

    public List<Integer> inorderTraversal(TreeNode root){
        List<Integer> res = new ArrayList<>();
        helper(root, res);
        return res;
    }

    public void helper(TreeNode root, List<Integer> res){
        if(root != null){
            if(root.left != null){
                helper(root.left, res);
            }
            res.add(root.val)
            if(root.right != null){
                helper(root.right, res);
            }
        }
    }

}
```
