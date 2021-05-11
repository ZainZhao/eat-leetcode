# 剑指 Offer 11 旋转数组的最小数字

```markdown
Label：二分法

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。
    输入：[3,4,5,1,2]  输入：[2,2,2,0,1]
    输出：1            输出：0
```

- API

```java
class Solution {
    public int minArray(int[] numbers) {
        Arrays.sort(numbers);
        return numbers[0];
    }
}
```

- 遍历

```java
class Solution {
    public int minArray(int[] numbers) {
        for (int i = 1; i < numbers.length; i++) {
            if (numbers[i] < numbers[i-1]) return numbers[i];
        } 
        return numbers[0];
    }
}
```

- 二分法

```java
class Solution {
   public int minArray(int[] numbers) {
        int l = 0, r = numbers.length - 1;
        while (l < r) {
            int mid = ((r - l) >> 1) + l; // 不用 l+r/2  是为了防止溢出
            //只要右边比中间大，那右边一定是有序数组
            if (numbers[r] > numbers[mid]) {
                r = mid;
            } else if (numbers[r] < numbers[mid]) {
                l = mid + 1;
            } else r--;  //去重
        }
        return numbers[l];
    }
}
```

