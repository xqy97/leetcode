### 题目描述
https://leetcode.cn/problems/sum-root-to-leaf-numbers/

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
var sumNumbers = function(root) {
    let num = ''
    let list = []
    let res = 0
    findNum(root,num, list)
    list.forEach(i => res += Number(i))
    return res
};

var findNum = function(root, num, list) {
    if(!root) {
        return
    }

    num += root.val

    if (!root.left && !root.right) {
        list.push(num)
        return
    }
    if (root.left) {
        findNum(root.left, num, list)
    }
    if (root.right) {
        findNum(root.right, num, list)
    }
}
```

### 复杂度
* 时间复杂度 O(N)
* 空间复杂度 O(height) height为二叉树高度, 最差O(N), 最优O(logN)
