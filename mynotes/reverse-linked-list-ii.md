https://leetcode-cn.com/problems/reverse-linked-list-ii/

反转从位置 m 到 n 的链表。请使用一趟扫描完成反转。

说明:
1 ≤ m ≤ n ≤ 链表长度。

示例:

输入: 1->2->3->4->5->NULL, m = 2, n = 4
输出: 1->4->3->2->5->NULL

代码：

```
class Solution{

    private boolean stop;//是否停止
    private ListNode left;//左指针

    /***
    *
    *
    *@param right 
    *@param m
    *@param n 
    */
    public void recurseAndReverse(ListNode right, int m, int n){
        // 特殊情况
        if(n == 1){ return;}
        // 右节点右移
        right = right.next;
        // 如果m大于1，left指针右移
        if(m > 1){
            this.left = this.left.next;
        }
        //
        this.recurseAndReverse(right, m - 1, n - 1);
        // 如果重合或者右指针跑到左指针的左边则结束
        if(this.left == right || right.next == this.left){
            this.stop = true;
        }
        // 如果没有结束则左右指针的值交换
        if(!stop){
            int t = this.left.val;
            this.left.val = right.val;
            right.val = t;
        // 左指针右移
            this.left = this.left.next;
        }
    }

    /**
    *
    *@param head 给定的链表
    *@param m 开头位置
    *@param n 结束位置
    */
    public ListNode reverseBetween(ListNode head, int m, int n){
        // 1. 初始化left指向head
        this.left  = head;
        // 2. 初始化stop为false
        this.stop = false;
        // 3. 执行 recurseAndReverse 方法，head作为右节点传入
        this.recurseAndReverse(head, m, n)
        // 4. 返回修改的节点
        return head;
    }

}

```
