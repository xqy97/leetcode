## 题目描述
https://leetcode.cn/problems/decode-string/

## 解题思路
把 ']' 当作出栈信号

## 代码
```javascript
/**
 * @param {string} s
 * @return {string}
 */
var decodeString = function(s) {
    let stack = []
    const isNum = (n) => Number(n) >= 0 && Number(n) <= 9
    let res=''
    for(i=0; i<s.length; i++) {
        if (s[i] !== ']') {
            stack.push(s[i])
        } else {
            let str=''
            let num=''
            let str2=''
            while(stack[stack.length - 1] !== '[') {
                str = stack[stack.length - 1] + str
                stack.length--
            }
            stack.length--
            while(isNum(stack[stack.length - 1])) {
                num = stack[stack.length - 1] + num
                stack.length--
            }
            while(Number(num) > 0) {
                str2 = str2 + str
                num--
            }
            stack.push(str2)
        }
    }
    for(i=0;i<stack.length;i++) {
        res= res+stack[i]
    }
    return res
};
```
