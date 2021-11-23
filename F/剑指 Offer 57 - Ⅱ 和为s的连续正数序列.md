## 剑指 Offer 57 - Ⅱ 和为s的连续正数序列

```markdown
Label：滑动窗口
输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。
序列内的数字由小到大排列，不同序列按照首个数字从小到大排列
    输入：target = 15
    输出：[[1,2,3,4,5],[4,5,6],[7,8]]
```

- 滑动窗口

```java

class Solution {
    public int[][] findContinuousSequence(int target) {
        List<int[]> vec = new ArrayList<int[]>();
        int l = 1, r = 2;
        while ( l < r) {
            int sum = (l + r) * (r - l + 1) / 2;
            if (sum == target) {
                int[] res = new int[r - l + 1];
                for (int i = l; i <= r; ++i) {
                    res[i - l] = i;
                }
                vec.add(res);
                l++;
            } else if (sum < target) {
                r++;
            } else {
                l++;
            }
        }
        return vec.toArray(new int[vec.size()][]);
    }
}
```

- 暴力枚举

```java
class Solution {
    public int[][] findContinuousSequence(int target) {
        List<List<Integer>> re = new ArrayList<>();

        for (int start = 1; start < target/2 + 1; start++) {
            List<Integer> list = new ArrayList<>();
            list.add(start);
            int sum = start;
            int curr = start;
            while (sum <= target) {
                if (sum == target) {
                    re.add(list);
                    break;
                }else {
                    curr++;
                    sum += curr;
                    list.add(curr);
                }
            }
        }
        int[][] reArray = new int[re.size()][];

        for (int i = 0; i < re.size(); i++) {
            reArray[i] = new int[re.get(i).size()];
            for (int j = 0; j < re.get(i).size(); j++) {
                reArray[i][j] = re.get(i).get(j);
            }
        }
        return reArray;
    }
}
```

