## 题目描述
https://leetcode.cn/problems/linked-list-cycle-ii/## 解题思路

## 解法一 哈希表

### 代码
```javascript
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var detectCycle = function(head) {
        const list = new Set()

        while(head) {
            if(list.has(head)){

                return head
            }

            list.add(head)
            head = head.next

        }
        return null
    };
```

### 复杂度
* 时间复杂度 O(n)
* 空间复杂度 O(n)

## 解法二 双指针

### 解题思路
- 快慢指针找到相遇点，快指针速度2，慢指针速度1，快指针在环中
  以速度1追逐慢指针，所以快慢指针一定会相遇
- 计算相遇点到入环的距离（没想出来看的答案）

### 代码
```javascript
var detectCycle = function(head) {
    if (head === null) {
        return null;
    }
    let slow = head, fast = head;
    while (fast !== null) {
        slow = slow.next;
        if (fast.next !== null) {
            fast = fast.next.next;
        } else {
            return null;
        }
        if (fast === slow) {
            let ptr = head;
            while (ptr !== slow) {
                ptr = ptr.next;
                slow = slow.next;
            }
            return ptr;
        }
    }
    return null;
};

```

### 复杂度
* 时间复杂度 O(n)
* 空间复杂度 O(1)
