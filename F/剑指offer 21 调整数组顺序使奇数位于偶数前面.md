## 剑指offer 21 调整数组顺序使奇数位于偶数前面

```markdown
Label：双指针

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。
    输入：nums = [1,2,3,4]
    输出：[1,3,2,4] 
    注：[3,1,2,4] 也是正确的答案之一。
```

- 头尾指针

```java
class Solution {
    public int[] exchange(int[] nums) {
        int odd = 0; // left
        int even = nums.length -1; // right

        while (odd < even) {
            while (odd < even && nums[odd] % 2 == 1) {
                odd++;
            } 

            while (odd < even && nums[even] % 2 == 0) {
                even--;
            }
            // 交换
            int temp = nums[odd];
            nums[odd] = nums[even];
            nums[even] = temp;
            odd++;
            even--;
        }

        return nums;
    }
}
```

