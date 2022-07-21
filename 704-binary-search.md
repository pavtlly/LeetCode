## 题意
#### 给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target  ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。
---
## 题解
#### 经典二分查找

#### python循环代码
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (right - left) // 2 + left
            num = nums[mid]
            if num == target:
                return mid
            elif num > target:
                right = mid - 1
            else:
                left = mid + 1
        return -1
```
#### python递归代码
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        def binary_search(i:int, j:int):
            if i > j: return -1
            mid = (i + j) // 2
            if target == nums[mid]: return mid
            elif target > nums[mid]: return binary_search(mid + 1, j)
            else: return binary_search(i, mid - 1)

        return binary_search(0, len(nums)-1)

```