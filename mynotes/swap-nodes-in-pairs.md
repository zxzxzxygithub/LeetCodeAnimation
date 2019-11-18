https://leetcode-cn.com/problems/swap-nodes-in-pairs/

题目描述
给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。

你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

代码

```
class Solution{

    /**
    *
    *@param head给定的链表
    */
    public ListNode swapPairs(ListNode head){
        // 1. 过滤边界条件：head为空，或者head的next节点为空，即只有一个节点
        if(head == null || head.next == null){
            return head;
        }
        // 2. 初始化一个栈
        Stack<ListNode> stack = new Stack<ListNode>();
        // 3. 初始化一个链表p
        ListNode p = new ListNode(-1);
        // 4. 初始化变量cur指向head
        ListNode cur = head;
        // 5. p赋值给head
        head = p;
        // 6. 进行循环,cur指针不为空，或者cur的next节点不为空，即cur至少为倒数第二个节点
        while(cur != null && cur.next != null){
            // 6.1 将两个节点放入stack中
            stack.add(cur);
            stack.add(cur.next);
            // 6.2 当前节点向前走两步
            cur = cur.next.next;
            // 6.3 从stack中弹出一个节点，作为p的下一个节点
            p.next = stack.pop();
            // 6.4 p节点移动到这个节点
            p = p.next
            // 6.5 再从stack中弹出一个节点，作为p的下一个节点
            p.next = stack.pop();
            // 6.6  p节点移动到这个节点
            p = p.next;
        }
        // 如果cur节点不为空，则p的下一个节点指向它（链到p的下一个节点）
        if(cur != null ){
            p.next = cur;
        }else{
            p.next = null;
        }
        //
        return head.next;
    }

}

```
