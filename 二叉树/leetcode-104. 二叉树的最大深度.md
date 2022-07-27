### 题目描述
https://leetcode.cn/problems/maximum-depth-of-binary-tree/
### 解题思路
- 递归DFS

### 代码
```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var maxDepth = function(root) {
    if(!root) {
        return 0
    }
    let h1 = 1 + maxDepth(root.left)
    let h2 = 1 + maxDepth(root.right)
    return Math.max(h1,h2)
};
```

### 复杂度
* 时间复杂度 O(n)
* 空间复杂度 O(height) height为二叉树高度
