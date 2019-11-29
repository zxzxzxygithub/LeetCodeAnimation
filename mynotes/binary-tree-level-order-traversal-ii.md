https://leetcode-cn.com/problems/binary-tree-level-order-traversal-ii/

二叉树的层次遍历 II

给定一个二叉树，返回其节点值自底向上的层次遍历。 （即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历）

例如：
给定二叉树 [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其自底向上的层次遍历为：

[
  [15,7],
  [9,20],
  [3]
]

代码：

```
class Solution{
public:
    vector<vector<int>> levelOrderBottom(TreeNode* root){
        vector<vector<int>> res;
        levelorder(root, 0, res);
        return vector<vector<int>>(res.rbegin(),res.end())
    }  

    void levelorder(TreeNode* node, int level, vector<vector<int>>& res){
        if(!node){return;}
        if(res.size() == level){
            res.push_back({});
        }
        res[level].push_back(node->val);
        if(node->left){levelorder(node->left, level + 1, res)};
        if(node->right){levelorder(node->right, level + 1, res)};
    }   
}

```
