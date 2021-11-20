## 剑指 Offer 56 Ⅰ 数组中数字出现的次数

```markdown
Label：位运算
一个整型数组 nums 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

    输入：nums = [4,1,4,6]
    输出：[1,6] 或 [6,1]

    输入：nums = [1,2,10,4,1,4,3,3]
    输出：[2,10] 或 [10,2]
```

```java
class Solution {
    public int[] singleNumbers(int[] nums) {
        int x = 0, y = 0, n = 0, m = 1;
        for(int num : nums)               // 1. 遍历异或
            n ^= num;
        while((n & m) == 0)               // 2. 循环左移，计算 m（取最低的为1的数）
            m <<= 1;
        for(int num: nums) {              // 3. 遍历 nums 分组
            if((num & m) != 0) x ^= num;  // 4. 当 num & m != 0
            else y ^= num;                // 4. 当 num & m == 0
        }
        return new int[] {x, y};          // 5. 返回出现一次的数字
    }
}
```

