# 剑指 Offer 05 替换空格

```markdown
Label：字符串

输入：s = "We are happy."
输出："We%20are%20happy."
```

- API

```java
class Solution {
    public String replaceSpace(String s) {
        s = s.replaceAll(" ", "%20");
        return s;
    }
}
```

- 遍历

```java
class Solution {
    public String replaceSpace(String s) {
        StringBuilder sb = new StringBuilder();
        for(int i = 0 ; i < s.length(); i++){
            char c = s.charAt(i);
            if(c == ' ') sb.append("%20");
            else sb.append(c);
        }
        return sb.toString();
    }
}
```

