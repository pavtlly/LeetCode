## 题意
#### 在时间 t 添加一个新请求，返回过去 3000 毫秒内发生的所有请求数（包括新请求）
---
## 题解
#### 将请求加入队列，如果队头元素请求的时间在 $[t-3000,t]$ 之外 就不断出队
```python
class RecentCounter:
    def __init__(self):
        self.q = deque()

    def ping(self, t: int) -> int:
        self.q.append(t)
        # 把目前队列中不符合[t-3000, t]的请求时间剔除出去
        while self.q[0] < t - 3000:
            self.q.popleft()
        return len(self.q)
```