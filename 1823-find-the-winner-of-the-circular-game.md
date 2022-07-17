## 题意
#### 经典约瑟夫问题，按题目要求移动
---
## 题解
#### 直接通过队列模拟过程
#### python代码
```python
class Solution:
    def findTheWinner(self, n: int, k: int) -> int:
        q = deque(range(1, n + 1))
        while len(q) > 1:
            for _ in range(k - 1):
                q.append(q.popleft())
            q.popleft()
        return q[0]
```