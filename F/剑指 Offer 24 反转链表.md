# 剑指 Offer 24 反转链表

```markdown
Label：链表
定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
```

- 递归

```java
class Solution {
    public ListNode reverseList(ListNode head) {
	
		if(head == null || head.next == null) {
			return head;
		}
		
		ListNode  reverseHead = reverseList(head.next);  // 要一直返回，这个值从最底层开始就是不变的
		
		head.next.next = head;
		head.next = null;  // 防止 顶层 出现 cycle

		return reverseHead;

    }
}
```

