# 剑指 Offer 38 字符串的排列

```markdown
Label：回溯
输入一个字符串，打印出该字符串中字符的所有排列。
你可以以任意顺序返回这个字符串数组，但里面不能有重复元素

输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
```

- HashSet

```java
class Solution {
    public String[] permutation(String s) {
        HashSet<String> re = new HashSet<>(); 
        int[] mark = new int[s.length()];
        dfs(re, mark, new StringBuffer(), s);    
        return re.toArray(new String[re.size()]);
    }

    private void dfs(HashSet<String> re, int[] mark, StringBuffer sb, String str) {
        if (sb.length() == str.length()) {
            re.add(sb.toString());
        }
        for (int i = 0; i < str.length(); i++) {
            if (mark[i] == 0) {
                mark[i] = 1;
                sb.append(str.charAt(i));
                dfs(re, mark, sb, str);
                sb.deleteCharAt(sb.length() - 1);
                mark[i] = 0;
            }
        }
    }
}
```

> 也可以排序之后做一些剪枝