## 剑指 Offer 62 圆圈中最后剩下的数字.md

```markdown
Label：数组
0,1,···,n-1这n个数字排成一个圆圈，从数字0开始，每次从这个圆圈里删除第m个数字（删除后从下一个数字开始计数）。求出这个圆圈里剩下的最后一个数字。

例如，0、1、2、3、4这5个数字组成一个圆圈，从数字0开始每次删除第3个数字，则删除的前4个数字依次是2、0、4、1，因此最后剩下的数字是3。
```

- bfs

```java
class Solution {
    public int lastRemaining(int n, int m) {
        ArrayList<Integer> list = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            list.add(i);
        }

        int removeIndex = m-1;
        while (list.size()!=1) {
            
            if (removeIndex < list.size()) {
                list.remove(removeIndex);
            } else {
                removeIndex = removeIndex % list.size();
                list.remove(removeIndex);
            }
            
            removeIndex = removeIndex + m -1;
        }
        return list.get(0);
    }
}
```

- dfs（约瑟夫问题）

```java
class Solution {
    public int lastRemaining(int n, int m) {
        return f(n, m);
    }

    public int f(int n, int m) {
        if (n == 1) {
            return 0;
        }
        int x = f(n - 1, m);
        return (m + x) % n;
    }
}
```



