https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/

示例：

```
给定一个链表: 1->2->3->4->5, 和 n = 2.

当删除了倒数第二个节点后，链表变为 1->2->3->5.
```

代码：

```
/**
 *@param head 头节点
 *@param n 倒数第n个节点
 */
public ListNode  removeNthFromEnd(ListNode head, int n){
    // 1. 新建一个节点
    ListNode dummy = new ListNode(0);
    // 2. 将该节点的下一个节点指向头节点
    dummy.next = head;
    // 3. 新建一个变量first，存放dummy节点
    ListNode first = dummy;
    // 4. 新建一个变量second，存放dummy节点
    ListNode second = dummy;
    // 5. 将first指针向右移动n个节点
    for(int i = 1; i <= n + 1; i++){
        first = first.next;
    }
    // 6. 执行循环，判断first是否为空，当first不为空的时候
    while(first != null){
        // 将first节点的next指针指向自己，直到first移动到末尾
        first = first.next;
        // 将second节点的next指针指向自己
        second = second.next;
    }
    // 7.删除第n个节点
    second.next = second.next.next;
    // 返回头节点
    return dummy.next;
}
```
