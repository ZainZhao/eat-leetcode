## 剑指 Offer 53 - Ⅱ 0~n-1中缺失的数字

```markdown
Label：数组

一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。
    输入: [0,1,2,3,4,5,6,7,9]
    输出: 8
```

- 二分法
```java
class Solution {
    public int missingNumber(int[] nums) {
        int left = 0;
        int right = nums.length;
        
        while (left < right) {
            int mid = (left + right) / 2;
            if (nums[mid] != mid) {
                right = mid;
            }else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

- 位运算

```java
class Solution {
    public int missingNumber(int[] nums) {
        int re = 0;
        int i = 0;
        for (; i < nums.length; i++) {
            re ^= nums[i];
            re ^= i;
        }
        re ^= i; // 缩了一位，所以要再异或 一位更大的index
        return re;
    }
}
```

