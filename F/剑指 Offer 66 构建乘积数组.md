## 剑指 Offer 66 构建乘积数组

```markdown
Label：数组、数学

给定一个数组 A[0,1,…,n-1]，请构建一个数组 B[0,1,…,n-1]，其中 B[i] 的值是数组 A 中除了下标 i 以外的元素的积, 即 B[i]=A[0]×A[1]×…×A[i-1]×A[i+1]×…×A[n-1]。不能使用除法。

输入: [1,2,3,4,5]
输出: [120,60,40,30,24]
```

- 左边连乘、右边连乘

```java
class Solution {
    public int[] constructArr(int[] a) {
        int[] res = new int[a.length];

        int currProduct = 1;
        // [1,2,3,4,5]
        for (int i = 0; i < a.length; i++) {
            res[i] = currProduct;   // 先乘左边的数(不包括自己)
            currProduct *= a[i]; 
        }
        
        currProduct = 1;
        // [1,1,2,6,24]
        for (int i = a.length - 1; i >= 0; i--) {
            res[i] *= currProduct;  // 再乘右边的数(不包括自己)
            currProduct *= a[i];
        }

        // [120,60,40,30,24]
        return res;
    }
}
```
