## 题目描述
https://leetcode.cn/problems/swap-nodes-in-pairs/

## 解题思路
- 看似两两交换，实际要用到三个节点

## 代码
```javascript
var swapPairs = function(head) {
    if(!head || !head.next) {
        return head
    }
    let newHead = new ListNode()
    newHead.next = head
    let temp = newHead
   
    while(temp.next && temp.next.next) {
        let p1 = temp.next
        let p2 = temp.next.next
        
        p1.next = p2.next
        temp.next = p2
        p2.next = p1

        temp = temp.next.next
        p1 = temp.next
    }

  
    return newHead.next
};
```

##复杂度
* 时间复杂度 O(n)
* 空间复杂度 O(1)
