## 题目描述
https://leetcode.cn/problems/convert-sorted-list-to-binary-search-tree/
## 解题思路
- 快慢指针查询链表中间节点
- 二分递归构造子树

## 代码
```javascript
var sortedListToBST = function trans(head) {
    const node = {};
    if (!head) {
        return null;
    }

    let slow = head;
    let fast = head;
    let last = head;

    while (fast && fast.next) {
        last = slow;
        slow = slow.next;
        fast = fast.next;
        fast = fast.next;
    }
    node.val = slow.val;

    node.left = null;

    if (last !== slow) {

        last.next = null;
        node.left = trans(head);
    }
    node.right = trans(slow.next);

    return node;
};
```

##复杂度
* 时间复杂度 O(nlogn)
* 空间复杂度 O(logn)
