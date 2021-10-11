## 剑指 Offer  53-Ⅰ 在排序数组中查找数字 Ⅰ

```markdown
Label：二分法

统计一个数字在排序数组中出现的次数。

输入: nums = [5,7,7,8,8,10], target = 8
输出: 2
```

- 二分法

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0,right = nums.length - 1;
        int count = 0;
        while (left < right) {
            int mid = (left + right) / 2;
            if(nums[mid] >= target)
                right = mid;
            if(nums[mid] < target)
                left = mid + 1;
        }

        while(left < nums.length && nums[left++] == target) // 短距离搜索
            count++;
            
        return count;
    }
}
```

