## 题目描述
https://leetcode.cn/problems/intersection-of-two-linked-lists/## 解题思路
## 解题思路
- 双指针分别遍历 a->b, b->a, 如果相遇则有交点

## 代码
```javascript
/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
var getIntersectionNode = function (headA, headB) {
        if (!headA || !headB) return null;

        let pA = headA,
            pB = headB;
        while (pA !== pB) {
            pA = pA === null ? headB : pA.next;
            pB = pB === null ? headA : pB.next;
        }
        return pA;
    };
```

## 复杂度
* 时间复杂度 O(m+n)
* 空间复杂度 O(1)
