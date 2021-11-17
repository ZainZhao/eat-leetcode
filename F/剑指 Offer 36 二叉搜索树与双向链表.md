## 剑指 Offer 36 二叉搜索树与双向链表

```markdown
Label：二叉搜索树
输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。
```

```java
class Solution {
    Node head, pre;
    public Node treeToDoublyList(Node root) {
        if (root == null) return null;
        dfs(root);
        pre.right = head;
        head.left =pre;

        return head;

    }

    public void dfs(Node cur){
        if(cur == null) return;

        dfs(cur.left);

        // pre用于记录双向链表中位于cur左侧的节点，
        if (pre == null) head = cur;
        else pre.right = cur; // 连接当前节点
       
        cur.left = pre;
        pre = cur;

        dfs(cur.right);//全部迭代完成后，pre指向双向链表中的尾节点
    }
}
```



