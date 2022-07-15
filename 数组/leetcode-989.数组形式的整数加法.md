## 题目描述
https://leetcode.cn/problems/add-to-array-form-of-integer/

## 解题思路

###逐位相加，记录进位


####难点
1. 数字怎么按位拆分
   * **数字不用拆分**
    * **num[i] + k % 10 先相加再%10**
2. 数组和数字位数不同时怎么处理
   * 开始打算取位数最多的，其实只用对没加完的数字单独处理
3. 进位处理
    * 加到数字上
    
####js代码
```javascript
  var addToArrayForm = function(num, k) {
  const res = []
    
  for(let i = num.length - 1; i>=0; i--) {
      let sum = num[i] + k % 10
      k = Math.floor(k / 10)
      if (sum > 9) {
        k++
        res.push(sum % 10)
      } else {
        res.push(sum)
      }
  }
  while(k) {
      res.push(k%10)
      k = Math.floor(k/10)
  }
  return res.reverse()
  
};
```
####复杂度
* 时间复杂度 O(max(num.length, log k))
* 空间复杂度 O(1)

## 加法模版
```
当前位 = (A 的当前位 + B 的当前位 + 进位carry) % 10

while ( A 没完 || B 没完)
A 的当前位
B 的当前位

    和 = A 的当前位 + B 的当前位 + 进位carry

    当前位 = 和 % 10;
    进位 = 和 / 10;

判断还有进位吗
```



     
  
