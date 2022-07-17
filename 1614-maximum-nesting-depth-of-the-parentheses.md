## 题意
#### 给定一个字符串去盘点嵌套了几层括号
---
## 题解
#### 利用栈来保存当前嵌套深度 "(" 进栈; ")" 弹栈; 其他字符 直接跳过，每次进栈更新下答案
#### python代码
```python
class Solution:
    def maxDepth(self, s: str) -> int:
        ans, size = 0, 0
        for ch in s:
            if ch == '(':
                size += 1
                ans = max(ans, size)
            elif ch == ')':
                size -= 1
        return ans
```