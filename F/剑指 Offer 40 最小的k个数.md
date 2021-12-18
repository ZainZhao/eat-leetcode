## 剑指 Offer 40 最小的k个数

```markdown
Label：堆
输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。
输入：arr = [3,2,1], k = 2
输出：[1,2] 或者 [2,1]
```

- 排序

```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
       Arrays.sort(arr);
        int[] re = new int[k];
        System.arraycopy(arr,0,re,0,k);

        return re;
    }
}
```

- 堆

```java
class Solution {
public int[] smallestK(int[] arr, int k) {
        int[] vec = new int[k];
        if (k == 0) { // 排除 0 的情况
            return vec;
        }

        // Comparator.reverseOrder() 建立小根堆
        PriorityQueue<Integer> queue = new PriorityQueue<Integer>((a,b)->(a-b)); 
        // 入堆
        for (int i = 0; i < arr.length; ++i) {
            queue.offer(arr[i]);
        }  
        // 出堆
        for (int i = 0; i < k; ++i) {
            vec[i] = queue.poll();
        }
        return vec;
    }
}
```

