## 剑指offer 20 表示数值的字符串

```markdown
Label：字符串
请实现一个函数用来判断字符串是否表示数值（包括整数和小数）。
数值（按顺序）可以分成以下几个部分：
    1.若干空格
    2.一个 小数 或者 整数
    3.（可选）一个 'e' 或 'E' ，后面跟着一个 整数
    4.若干空格
小数（按顺序）可以分成以下几个部分：
1.（可选）一个符号字符（'+' 或 '-'）
2. 下述格式之一：
	1. 至少一位数字，后面跟着一个点 '.'
	2. 至少一位数字，后面跟着一个点 '.' ，后面再跟着至少一位数字
	3. 一个点 '.' ，后面跟着至少一位数字
整数（按顺序）可以分成以下几个部分：
1. （可选）一个符号字符（'+' 或 '-'）
2. 至少一位数字
部分数值列举如下：["+100", "5e2", "-123", "3.1416", "-1E-16", "0123"]
部分非数值列举如下：["12e", "1a3.14", "1.2.3", "+-5", "12e+5.4"]
```

```java
class Solution {
    // ‘.’出现正确情况：只出现一次，且在e的前面
    // ‘e’出现正确情况：只出现一次，且出现前有数字
    // ‘+’‘-’出现正确情况：只能在开头和e后一位
    public boolean isNumber(String s) {
        if (s == null || s.length() == 0) return false;
        s = s.trim();
        boolean numFlag = false;
        boolean dotFlag = false;
        boolean eFlag = false;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) >= '0' && s.charAt(i) <= '9') { //判定为数字，则标记numFlag
                numFlag = true;
            } else if (s.charAt(i) == '.' && !dotFlag && !eFlag) { //判定为. 需要没出现过.并且没出现过e
                dotFlag = true;
                //判定为e，需要没出现过e，并且出过数字了
            } else if ((s.charAt(i) == 'e' || s.charAt(i) == 'E') && !eFlag && numFlag) {
                eFlag = true;
                numFlag = false;//为了避免123e这种请求，出现e之后就标志为false
                //判定为+-符号，只能出现在第一位或者紧接e后面
            } else if ((s.charAt(i) == '+' || s.charAt(i) == '-') && (i == 0 || s.charAt(i - 1) == 'e' || s.charAt(i - 1) == 'E')) {
     			continue;
            } else { //其他情况，都是非法的
                return false;
            }
        }
        return numFlag;
    }
}
```





