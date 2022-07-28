### 题目描述
https://leetcode.cn/problems/same-tree/

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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {boolean}
 */
var isSameTree = function(p, q) {
    if(p == null && q == null)
        return true;
    if(p == null || q == null)
        return false;
    if(p.val != q.val)
        return false;
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
}
```

### 复杂度
* 时间复杂度 O(N)
* 空间复杂度 O(height) height为二叉树高度, 最差O(N), 最优O(logN)
