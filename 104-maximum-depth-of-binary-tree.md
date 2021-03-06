## 题意
#### 给定一颗二叉树，找出其最大深度
---
## 题解
#### 按照二叉树的性质，不断往左右子树递归下去，从左右子树中选择深度大的那个，再加上自己本身节点（$+1$）
#### c++代码
```c++
class Solution {
public:
    int ans = 0;
    void dfs(TreeNode *node, int dep) {
        if(node == NULL) return ;
        dfs(node->left, dep + 1);
        dfs(node->right, dep + 1);
        ans = max(ans, dep);
    }

    int maxDepth(TreeNode* root) {
        dfs(root, 1);
        return ans;
    }
};
```
#### python代码
```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root: return 0
        # 利用定义 计算左右子树的最大深度
        left = self.maxDepth(root.left)
        right = self.maxDepth(root.right)
        # 整棵树的最大深度等于左右子树的最大深度取最大值 再加上根节点自己
        return max(left, right) + 1
```