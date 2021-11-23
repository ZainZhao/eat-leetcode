## 剑指 Offer 65 不用加减乘除做加法

```markdown
Label：位运算
写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号。
```

<img src="pic\剑指65.png" alt="Picture1.png" style="zoom:50%;" />

```java
class Solution {
    public int add(int a, int b) {
        while(b != 0) { // 当进位为 0 时跳出 
            int carry = (a & b) << 1;  
            a ^= b; // a = 非进位和
            b = carry; // b = 进位
        }
        return a;
    }
}
```



