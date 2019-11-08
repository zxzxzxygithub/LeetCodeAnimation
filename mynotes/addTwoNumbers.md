https://github.com/MisterBooo/LeetCodeAnimation/blob/master/notes/LeetCode%E7%AC%AC2%E5%8F%B7%E9%97%AE%E9%A2%98%EF%BC%9A%E4%B8%A4%E6%95%B0%E7%9B%B8%E5%8A%A0.md

示例：

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807

code:

```
class Solution{
    public:
     /*
      *@param l1 链表1
      *@param l2 链表2
      */
     ListNode* addTwoNumbers(ListNode* l1,ListNode* l2){
         // 1.初始化两个变量，*p1和*p2,分别将l1，和l2赋值给他们   
         ListNode *p1 = l1, *p2 = l2;
         // 2.新建一个ListNode对象
         ListNode *dummyHead = new ListNode(-1);
         // 3.新建一个指针指向这个变量
         ListNode* cur = dummyHead;
         // 4.新建一个变量carried
         int carried = 0;
         // 5.while循环，p1或p2？
         while(p1|| p2){
             // 5.1 初始化变量a,如果p1还没遍历完则取p1的值
             int a = p1 ? p1->val : 0;
             // 5.2 初始化变量b,如果p2还没遍历完则取p2的值
             int b = p2 ? p2->val : 0;
             // 5.3 新建一个ListNode对象，将a,b,carried相加之后取模的结果给他
             //     并让cur的next指针指向它
             cur -> next = new ListNode((a+b+carried) % 10)
             // 5.4 将a，b，carried之和除以10的结果赋值给carried
             carried = (a + b + carried) / 10;
             // 5.5 将cur指针指向cur的next
             cur = cur -> next;
             // 5.6 将p1指针指向p1的next
             p1 = p1 ? p1 -> next : NULL; 
             //  5.7 将p2指针指向p2的next
             p2 = p2 ? p2 -> next : NULL; 
         }
         // 6. 循环完之后看carried值是否大于0，如果大于0则新建一个listnode，将1赋值过去，否则指向NULL
         cur -> next = carried ? new ListNode(1) : NULL;
         // 7. 将dummyHead的next节点赋值给ret节点
         ListNode* ret = dummyHead->next;
         // 8. 删除dummyHead节点
         delete dummyHead;
         // 9. 返回ret节点
         return ret;

     }
}

```
