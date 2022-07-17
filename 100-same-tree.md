## 题意
#### 给定两棵二叉树的根节点，验证两棵二叉树是否相同。
#### 树的结构和节点具有相同的值，则我们认为是相同的。
---
## 题解
### 递归下去 有这三种情况：
#### 1. 两树都空返回真
#### 2.一树空一树非空返回假
#### 3. 两树都不空时，若根节点值不同返回假; 否则返回左子树是否相同 and 右子树是否相同

#### python代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if not p and not q:
            return True
        if not p or not q:
            return False
        if p.val != q.val:
            return False
        return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```