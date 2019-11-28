https://leetcode-cn.com/problems/binary-tree-zigzag-level-order-traversal/


二叉树的锯齿形层次遍历


给定一个二叉树，返回其节点值的锯齿形层次遍历。（即先从左往右，再从右往左进行下一层遍历，以此类推，层与层之间交替进行）。

例如：
给定二叉树 [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7

返回锯齿形层次遍历如下：

[
  [3],
  [20,9],
  [15,7]
]

```
class Solution{
    public List<List<Integer>> zigzagLevelOrder(TreeNode root){
        List<List<Integer>> result = new ArrayList<>();
        if(root == null){
            return result;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        //
        boolean isReverse = false;
        while(!queue.isEmpty()){
            LinkedList<Integer> oneLevel = new LinkedList<>();
            //
            int count = queue.size()
            for(int i = 0; i < count; i ++){
                TreeNode node = queue.poll();
                if(!isReverse){
                    oneLevel.add(node.val);
                }else{
                    oneLevel.addFirst(node.val);
                }
                if(node.left != null){
                    queue.add(node.left);
                }
                if(node.right != null){
                    queue.add(node.right);
                }
            }
            isReverse = !isReverse
            result.add(oneLevel)
        }
        return result;
    }

}

```
