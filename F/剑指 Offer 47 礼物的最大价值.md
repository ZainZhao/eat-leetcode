## 剑指 Offer 47 礼物的最大价值

```markdown
Label：动态规划
在一个 m*n 的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值（价值大于 0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向右或者向下移动一格、直到到达棋盘的右下角。给定一个棋盘及其上面的礼物的价值，请计算你最多能拿到多少价值的礼物？
    输入: 
    [
      [1,3,1],
      [1,5,1],
      [4,2,1]
    ]
    输出: 12
    解释: 路径 1→3→5→2→1 可以拿到最多价值的礼物
```

- 二维dp（标准）

```java
class Solution {
    public int maxValue(int[][] grid) {
        int dp[][] = new int[grid.length][grid[0].length];
        // 初始化
        dp[0][0] = grid[0][0];
        for (int i = 1; i < grid[0].length; i++ ) {
            dp[0][i] = dp[0][i-1] + grid[0][i];
        }
        for (int i = 1; i < grid.length; i++ ) {
            dp[i][0] = dp[i-1][0] + grid[i][0];
        }
    
        for (int i = 1; i < grid.length; i++) {
            for (int j = 1; j < grid[0].length; j++) {
               dp[i][j] = Math.max(dp[i-1][j],dp[i][j-1]) +  grid[i][j];
            }
        }
        return dp[grid.length-1][ grid[0].length-1];
    }
}
```

- 一维dp（未看）

```java
class Solution {
    public int maxValue(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int []dp = new int[n];
        for(int i = 0; i < m; i++){
            dp[0] = dp[0] + grid[i][0];
            for(int j = 1; j < n; j++){
                dp[j] = Math.max(dp[j], dp[j-1]) + grid[i][j];
            }
        }
        return dp[n-1];
    }
}
```



