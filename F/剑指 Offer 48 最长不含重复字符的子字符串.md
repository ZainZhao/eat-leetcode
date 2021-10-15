## 剑指 Offer 48 最长不含重复字符的子字符串

```markdown
Lable：双指针
请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。
    输入: "abcabcbb"
    输出: 3 
    解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

- 双指针

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length(); 
        if(n == 0) {   
            return 0;
        }
        //  本题中字符串只含有英文字母，符号和数字，所以可以使用数组来代替哈希表，提高效率。
        int[] num = new int[128];   
        int res = 0;
        int left = 0, right = 0;
        char[] cs = s.toCharArray();

        while(right < n) {
            //每次循环都将右侧指针向前移动一位，并将右侧指针所指向的字符的数量增加1
            num[(byte) cs[right]]++;

            //如果此时右侧指针所对应的字符的数量超过1，表示已经有了重复字符，将左指针右移
            while(num[(byte) cs[right]] > 1) {
                num[(byte) cs[left++]]--; 
            }
            //更新结果，取之前的结果与当前窗口长度的最大值
            res = Math.max(res, right - left + 1);

            right++;
        }
        return res;
    }
}
```