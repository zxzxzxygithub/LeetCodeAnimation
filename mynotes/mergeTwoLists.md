
https://leetcode-cn.com/problems/merge-two-sorted-lists/solution/he-bing-liang-ge-you-xu-lian-biao-by-leetcode/

将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的

示例：

输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4

代码：

class Solution{
    /**
    *
    *@param l1,l2 给定的两个链表
    */
    public ListNode mergeTwoLists(ListNode l1, ListNode l2){
        // 1. 如果链表1为空则返回链表2
        if(l1 == null){
            return l2;
        }
        // 2. 如果链表2为空则返回链表1
        if(l2 == null){
            return l1;
        }
        // 3. 如果l1的值小于l2的值，则l1作为链表头，剩下的继续递归
        if(l1.val < l2.val){
            l1.next = mergeTwoLists(l1.next, l2)
            return l1;
            // 4. 反之则l2作为链表头，剩下的继续递归
        }else(l1.val < l2.val){
            l1.next = mergeTwoLists(l1.next, l2)
            return l2;
        }

    }
}
