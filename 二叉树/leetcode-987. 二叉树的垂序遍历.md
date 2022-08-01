### 题目描述
https://leetcode.cn/problems/vertical-order-traversal-of-a-binary-tree/

### 解题思路
- dfs遍历每一个节点，记录每个节点的，colIndex, rowIndex, value
- 按列，行，值，把所有节点排序
- 同一行同一列的节点放进一个数组

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
 * @return {number[][]}
 */
var verticalTraversal = function(root) {
    let nodeList = []
    dfs(root, 0, 0, nodeList)
    nodeList.sort((pre, cur) => {
        if(pre[0] !== cur[0]) {
            return pre[0] - cur[0]
        } else if (pre[1] !== cur[1]) {
            return pre[1] - cur[1]
        } else {
            return pre[2] - cur[2]
        }
    })
    let res = []
    let lastCol = -Number.MAX_VALUE
    for(let node of nodeList) {
        if (node[0] !== lastCol) {
            lastCol = node[0]
            res.push([])
        }
        res[res.length - 1].push(node[2])
    }
    return res
}

const dfs = (node, row, col, nodes) => {
    if (node === null) {
        return;
    }
    nodes.push([col, row, node.val]);
    dfs(node.left, row + 1, col - 1, nodes);
    dfs(node.right, row + 1, col + 1, nodes);
}
```

### 复杂度
* 时间复杂度 O(nlogn)
* 空间复杂度 O(n)
