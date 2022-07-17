## 题意
#### 给定一个字符串，去删除最外层的括号，返回原语
---
## 题解
#### 题目要求我们删除最外层的括号，也就是每当有一组有效的括号（左右配对）时，我们需要删除最外层的括号。
#### 我们可以通过维护一个变量level来记录当前左括号的数量，遇到右括号，我们就计数减去1，如果level > 0，我们就将当前字符加入结果集，从而达到删除最外层括号的目的
#### python代码
```python
class Solution:
    def removeOuterParentheses(self, s: str) -> str:
        res, level = "", 0
        for c in s:
            if c == ')':
                level -= 1
            if level:
                res += c
            if c == '(':
                level += 1
        return res
```