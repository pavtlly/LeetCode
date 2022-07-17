## 题意
#### 给定一颗二叉树，求其前序遍历，前序遍历:根 左 右
---
## 题解
#### 按照递归的方式遍历二叉树即可 因为是根左右的关系，所以先输出每个遍历的节点 然后再从这个节点分别往左右子树遍历

#### python代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        def preorder(root: TreeNode):
            if not root: return
            res.append(root.val)
            preorder(root.left)
            preorder(root.right)

        res = list()
        preorder(root)
        return res
```