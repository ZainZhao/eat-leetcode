## 剑指 Offer 16 数值的整数次方

```markdown
Label：数学、dfs
实现 pow(x, n) ，即计算 x 的 n 次幂函数（即，xn）。不得使用库函数，同时不需要考虑大数问题。
	输入：x = 2.00000, n = 10
	输出：1024.00000

    输入：x = 2.00000, n = -2
    输出：0.25000
    解释：2-2 = 1/22 = 1/4 = 0.25
-100.0 < x < 100.0
-231 <= n <= 231-1
-104 <= xn <= 104
```

```java
class Solution {
    public double myPow(double x, int n) {
        
        if(n==0 || x==1.0) return 1.0;
        if(n==1) return x;
        if(n==-1) return 1.0/x;
      
        double res=myPow(x, n/2);
        res = res*res;

        //如果是奇数
        if((n & 1) == 1 && n > 0) res = res * x;   
        if((n & 1) == 1 && n < 0) res = res * 1/x; 
        
        return res;
    }
}
```

