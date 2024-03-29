# 剑指 Offer33 二叉搜索树的后续遍历序列

```markdown
Label：二叉树
输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 true，否则返回 false。假设输入的数组的任意两个数字都互不相同。
             5
            / \
           2   6
          / \
         1   3
    输入: [1,6,3,2,5]
    输出: false
    输入: [1,3,2,6,5]
    输出: true
```

- dfs

```java
class Solution {
    // 二叉搜索树中根节点的值大于左子树中的任何一个节点的值，小于右子树中任何一个节点的值，子树也是
    public boolean verifyPostorder(int[] postorder) {
        if (postorder.length < 2) return true;
        return verify(postorder, 0, postorder.length - 1); 
    }

    // 递归实现
    private boolean verify(int[] postorder, int left, int right){
        if (left >= right) return true; // 当前区域不合法的时候直接返回true就好

        int rootValue = postorder[right]; // 当前树的根节点的值

        int k = left;
        while (k < right && postorder[k] < rootValue){ // 从当前区域找到第一个大于根节点的，说明后续区域数值都在右子树中
            k++;
        }

        for (int i = k; i < right; i++){ // 进行判断后续的区域是否所有的值都是大于当前的根节点，如果出现小于的值就直接返回false
            if (postorder[i] < rootValue) return false;
        }

        // 当前树没问题就检查左右子树
        if (!verify(postorder, left, k - 1)) return false; // 检查左子树

        if (!verify(postorder, k, right - 1)) return false; // 检查右子树

        return true; // 最终都没问题就返回true
    }
}
```







- 单调栈（没看懂）

```java
class Solution {
    public boolean verifyPostorder(int[] postorder) {
        int top = -1, prev = Integer.MAX_VALUE;
        int[] stack = new int[postorder.length];
        for (int i = postorder.length - 1; i >= 0; i--) {
            if (postorder[i] > prev) return false;
            while (top != -1 && postorder[i] < stack[top]) prev = stack[top--];
            stack[++top] = postorder[i];
        }
        return true;
    }
}
```

