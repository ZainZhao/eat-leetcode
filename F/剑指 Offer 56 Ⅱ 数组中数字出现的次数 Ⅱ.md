## 剑指 Offer 56 Ⅱ 数组中数字出现的次数 Ⅱ

```markdown
Label：位运算
在一个数组 nums 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字。
    输入：nums = [9,1,7,9,7,9,7]
    输出：1
```

- 排序

```java
class Solution {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);
        for (int i =0; i<nums.length-3;i+=3) {
            if (nums[i] != nums[i+1]) {
                return nums[i];
            }
        }
        return nums[nums.length-1];
    }
}
```

- 统计

<img src="pic\剑指 Offer 56 Ⅱ.png" alt="Picture1.png" style="zoom: 25%;" />

```java
class Solution {
    public int singleNumber(int[] nums) {
        int[] counts = new int[32]; // int 为 32 位
        for(int num : nums) {         // 统计
            for(int j = 0; j < 32; j++) {
                counts[j] += num & 1; // 是否为 1
                num >>>= 1;
            }
        }
        int res = 0, m = 3;         // 对32位int的每一位求余
        for(int i = 0; i < 32; i++) {
            res <<= 1;
            res |= counts[31 - i] % m; // 注意是倒序
        }
        return res;
    }
}
```
