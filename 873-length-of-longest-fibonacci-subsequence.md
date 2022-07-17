## 题意
#### 给定一个严格递增的正整数序列，找到序列中最长的斐波那契式的子序列的长度。
#### 斐波那契式指类似 {1, 2, 3, 5, 8 ...}
---
## 题解
#### 最长上升子序列的变型题，通过dp[j][i]表示以arr[i]为斐波那契数列的最后一位，arr[j]为倒数第二位时的最长数列长度。转移方程的话，从i, j, k依次往前找 找到满足$arr[i] = arr[j] + arr[k]$的，$dp[j][i]=max(dp[j][i], dp[k][j] + 1)$, 当然暴力这样做 肯定会超时，我们可以通过hash去直接找到那个k，降低时间复杂度。
#### c++代码
```c++
class Solution {
public:
    int lenLongestFibSubseq(vector<int>& arr) {
        int n = arr.size(), res = 0;
    	vector<vector<int>> dp(n, vector<int>(n, 0));
        map<int, int> m;
        for (int i = 0; i < n; i++) m[arr[i]] = i;

        for (int i = 2; i < n; i++)
        for (int j = 1; j < i; j++) {
            // int k = m[arr[i] - arr[j]]; 这里会改变map的count
            if (m.count(arr[i] - arr[j])) {
                int k = m[arr[i] - arr[j]];
                if (k < j) dp[j][i] = max(dp[k][j] + 1, 3);
            }
            res = max(res, dp[j][i]);
        }
        return res >= 3 ? res : 0;
    }
};
```