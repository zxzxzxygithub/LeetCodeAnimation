https://leetcode-cn.com/problems/partition-list/

分隔链表

给定一个链表和一个特定值 x，对链表进行分隔，使得所有小于 x 的节点都在大于或等于 x 的节点之前。

你应当保留两个分区中每个节点的初始相对位置。

示例:

输入: head = 1->4->3->2->5->2, x = 3
输出: 1->2->2->4->3->5

```
class Solution{
    /**
    *
    *@param head 给定的链表
    *@param x 给定的链表中的一个值
    **/
    public ListNode partition(ListNode head, int x){
        // 1. 初始化一个哑节点before_head
        ListNode before_head = new ListNode(0);
        // 2. before_head 赋值给before节点
        ListNode before = before_head;
        // 3. 初始化一个哑节点after_head
        ListNode after_head = new ListNode(0);
        // 4. after_head 赋值给after节点
        ListNode after = after_head;
        // 5. 遍历给定节点
        while(head != null){
            // 5.1 如果当前节点小于给定节点，链到before的链表中
            if(head.val < x){
                before.next = head;
                before = before.next;
            }else{
            // 5.2 如果当前节点大于给定节点，链到after的链表中   
                after.next = head;
                after = after.next;
            }
            // 链表右移
            head = head.next;
        }
        // after节点收尾
        after.next = null;
        // before节点链到after链表
        before.next = after_head.next;
        // 返回新的链表
        return before_head.next;
    }
}
```

