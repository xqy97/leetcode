## 题目描述
https://leetcode.cn/problems/rotate-list/

## 解题思路
- 把最后一位移动到第一位 ===> 环形链
- 假设链表长度为n, 实际移动 m*n 次后，链表不变
- 移动k次，实际只需移动 k % n 次
- 找到新链表的最后一个节点断开 第（length - k % n）个节点.next = null


## 代码
```javascript
/**
 * @param {ListNode} head
 * @param {number} k
 * @return {ListNode}
 */
var rotateRight = function(head, k) {
        if (!head || !head.next || !k) {
            return head
        }
        let len = 1
        let p = head
        while(p.next) {
            len++
            p = p.next
        }
        if (k%len === 0) {
            return head
        }
        p.next = head // 形成环形链
        let index = len - k % len
        while(index) {
            p = p.next
            index--
        }
        let head2 = p.next
        p.next = null
        return head2
    };
```

##复杂度
* 时间复杂度 O(n)
* 空间复杂度 O(1)
