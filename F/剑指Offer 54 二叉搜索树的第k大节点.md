# 剑指Offer 54 二叉搜索树的第k大节点.md

```markdown
Lable：二叉树
 给定一棵二叉搜索树，请找出其中第k大的节点。
 输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
```

- 存取

```java
class Solution {
    public int kthLargest(TreeNode root, int k) {
        ArrayList<Integer> list = new ArrayList<>();
        // 先遍历一遍
        add(root, list);
        // 再取值
        return list.get(list.size()-k);
    }

    private void add(TreeNode root, ArrayList<Integer> list) {
        if (root == null) return;
        add(root.left,list);
        list.add(root.val);
        add(root.right,list);
    }
}
```

- 倒序遍历（取）

```java
class Solution {
    int res, k;
    public int kthLargest(TreeNode root, int k) {
        this.k = k;
        dfs(root);
        return res;
    }
    void dfs(TreeNode root) {
        if(root == null) return;

        dfs(root.right);

        if(k == 0) return ;

        if(--k == 0) res = root.val;

        dfs(root.left);
    }
}
```
