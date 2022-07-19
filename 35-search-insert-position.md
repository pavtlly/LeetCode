## 题意
#### 给定无重复元素的升序数组，查询target在数组中的位置，如果查不到的话，返回按顺序插入的位置
---
## 题解
#### 经典二分查找，如果没有找到，最后返回 $right + 1$ 可以自己画图理解一下，不断逼近，在小于和刚好大于它的位置插数
#### python代码
```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1

        while left <= right:
            middle = (left + right) // 2
            if nums[middle] < target:
                left = middle + 1
            elif nums[middle] > target:
                right = middle - 1
            else:
                return middle
        return right + 1
```