## 题意
#### 给定一个整数数组 $nums$ 和一个整数 $k$ ，求满足 $i < j$ 且 $|nums[i] - nums[j]| == k$ 的数目。
---
## 题解
#### 第一种做法就是两重for循环 暴力找，时间复杂度$O（n^2)$
#### python代码
```python
class Solution:
    def countKDifference(self, nums: List[int], k: int) -> int:
        res, n = 0, len(nums)
        for i in range(n):
            for j in range(i + 1, n):
                if abs(nums[i] - nums[j]) == k:
                    res += 1
        return res
```
#### 第二种就是用哈希映射，用dict的子类Counter，去进行计数。优化第二重循环
#### python代码
```python
class Solution:
    def countKDifference(self, nums: List[int], k: int) -> int:
        ans = 0
        m = Counter()
        for v in nums:
            ans += m[v - k] + m[v + k]
            m[v] += 1
        return ans
```