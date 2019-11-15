
https://leetcode-cn.com/problems/merge-k-sorted-lists/

合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

示例:

输入:
[
  1->4->5,
  1->3->4,
  2->6
]
输出: 1->1->2->3->4->4->5->6

python代码：

```
class Solution(object):
    # 输入参数lists表示一个链表集合
    def mergeKLists(self,lists):
        """
        :type lists:List[ListNode]
        :rtype ListNode
        """
        # 1. 定义一个节点数组nodes
        self.nodes = []
        # 2. 定义一个空链表
        head = point = ListNode(0)
        # 3.  遍历链表集合
        for l in lists:
            # 3.1.  遍历链表,讲链表中的各个节点赋值给nodes数组
            while l:
              self.nodes.append(l.val)
              l = l.next
        # 4. 对数组进行排序，然后遍历    
        for x in sorted(self.nodes):
            # 4.1 将数组组装成链表   
            point.next = ListNode(x)
            point = point.next
        return head.next;
```
