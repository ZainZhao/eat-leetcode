## 剑指 Offer 61扑克牌中的顺子

```markdown
Label：数组、排序
```

- 排序

```java
class Solution {
    public boolean isStraight(int[] nums) {
        Arrays.sort(nums);
        int count0 = nums.length-1;
        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] == 0) {
                count0++;
            }else {

                if (nums[i+1] == nums[i]) { // 出现 相等
                    return false;
                }

                count0 = count0 - (nums[i+1] -nums[i]); 

                if (count0 < 0) {
                    return false;
                }

            } 
        }
        return true;
    }
}
```

- 优化

```java
class Solution {
    public boolean isStraight(int[] nums) {
        int joker = 0;
        Arrays.sort(nums); // 数组排序
        for(int i = 0; i < 4; i++) {
            if(nums[i] == 0) joker++; // 统计大小王数量
            else if(nums[i] == nums[i + 1]) return false; // 若有重复，提前返回 false
        }
        return nums[4] - nums[joker] < 5; // 最大牌 - 最小牌 < 5 则可构成顺子
    }
}
```



