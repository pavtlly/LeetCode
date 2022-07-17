## 题意
#### 用哈希映射去进行记录
---
## 题解
#### 跑两边 第一次记出现次数 第二次判断出现次数为1的直接返回对应的下标
#### python代码
```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        n = len(s)
        dic = {}
        for i in range(n):
            if s[i] in dic:
                dic[s[i]] = dic[s[i]] + 1
            else:
                dic[s[i]] = 1

        for i in range(n):
            if dic[s[i]] == 1:
                return i
        return -1
```