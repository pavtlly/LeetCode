## 题意
#### 给定一颗二叉树，问是否存在从根节点到叶子节点路径上所有节点之和为targetSum的情况
---
## 题解
#### 遍历二叉树即可，遍历到叶子结点的时候判断下

#### python代码
#### 1.带返回值的写法
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False
        if not root.left and not root.right:
            return targetSum == root.val
        return self.hasPathSum(root.left, targetSum - root.val) or self.hasPathSum(root.right, targetSum - root.val)
```
#### 2.变量标记写法
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root: return False
        self.ans = False
        def dfs(rt: Optional[TreeNode], sum: int):
            if not rt.left and not rt.right:
                if sum == targetSum: self.ans = True
            if rt.left:
                dfs(rt.left, sum + rt.left.val)
            if rt.right:
                dfs(rt.right, sum + rt.right.val)
        dfs(root, root.val)
        return self.ans
```