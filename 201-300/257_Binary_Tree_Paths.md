### 257. Binary Tree Paths

Given a binary tree, return all root-to-leaf paths.

**Note:** A leaf is a node with no children.

**Example:**
```
Input:

   1
 /   \
2     3
 \
  5

Output: ["1->2->5", "1->3"]

Explanation: All root-to-leaf paths are: 1->2->5, 1->3
```

**Solution**
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def helper(self, node, ans, subset):
        if node is None:
            return

        if node.left is None and node.right is None:
            subset.append(str(node.val))
            ans.append("->".join(subset))
            subset.pop()
            return
        
        subset.append(str(node.val))
        self.helper(node.left, ans, subset)
        self.helper(node.right, ans, subset)
        subset.pop()

    def binaryTreePaths(self, root):
        """
        :type root: TreeNode
        :rtype: List[str]
        """
        if root is None:
            return []

        ans = []
        subset = []
        self.helper(root, ans, subset)

        return ans
```