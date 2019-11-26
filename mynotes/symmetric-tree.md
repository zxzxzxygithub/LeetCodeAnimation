
https://leetcode-cn.com/problems/symmetric-tree/

给定一个二叉树，检查它是否是镜像对称的。
例如，二叉树 [1,2,2,3,4,4,3] 是对称的。
    1
   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:
    1
   / \
  2   2
   \   \
   3    3

 ```
 public boolean isSymmetric(TreeNode node){
     return isMirror(root, root);
 }

 public boolean isMirror(TreeNode t1,TreeNode t2){
     // 1. 左右为空，true
     if(t1 == null && t2 == null){
         return true;
     }
    // 2. 任1为空，false
     if(t1 == null || t2 == null){
         return false;
     }
     return (t1.val == t2.val)
          && isMirror(t1.right, t2.left)
          && isMirror(t1.left, t2.right);

 }
 ```  
































