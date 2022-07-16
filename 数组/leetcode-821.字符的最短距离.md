## 题目描述
https://leetcode.cn/problems/shortest-distance-to-a-character/
## 解题思路

记录字符c出现的下标，遍历比较最短距离


###我的暴力解法（👎👎👎

####js代码
```javascript
/**
 * @param {string} s
 * @param {character} c
 * @return {number[]}
 */
var shortestToChar = function(s, c) {
        let indexList = []
        let res = []
        for(let i = 0; i < s.length; i++) {
            if (s[i] === c) {
                indexList.push(i)
                res[i] = 0
            }
        }
        let k = 0
        for(let i = 0; i < s.length; i++) {
            if(!indexList.includes(i)) {
                while(k+1 < indexList.length && Math.abs( indexList[k] - i) > Math.abs(indexList[k+1] - i)) {
                    k += 1
                }
                res[i] =  Math.abs( indexList[k] - i)
            }
        }
        return res
    };
```
####复杂度
* 时间复杂度 O(n)
* 空间复杂度 O(1)

###官方题解

- 双向遍历
- 问题可以转换成，对s的每个下标i，求 \
    s[i]  到其左侧最近的字符 cc 的距离\
    s[i]  其右侧最近的字符 cc 的距离 \
  这两者的最小值。
  
####难点：
在开始遍历的时候，不知道第一个等于目标字符的index在哪，为了简化逻辑，我们可以用 -n 或 2n 表示，这里 n 是 s 的长度。
确保每一位到index的距离 >= n
取n的话从右遍历，最小距离为1

####js代码
```javascript
var shortestToChar = function(s, c) {
    let n = s.length
    let res = new Array(n).fill(0)
    for(let i = 0, index = 2*n; i < s.length; i++) {
        if (s[i] === c) {
            index = i
        } else {
            res[i] = Math.abs(i - index)
        }
    }
    
    for(let i = s.length - 1,index = 2*n; i >= 0; i--) {
       if (s[i] === c) {
           index = i
       } else {
           res[i] = Math.min(res[i], Math.abs(i - index))
       }
    }
    return res
};
```
####复杂度
* 时间复杂度 O(n)
* 空间复杂度 O(1)



     
  
