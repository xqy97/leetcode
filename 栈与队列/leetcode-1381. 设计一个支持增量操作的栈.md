## 题目描述
https://leetcode.cn/problems/design-a-stack-with-increment-operation/

## 解题思路
用数组模拟栈，用变量记录栈顶位置


####js代码
```javascript
/**
 * @param {number} maxSize
 */
var CustomStack = function(maxSize) {
        this.res = new Array()
        this.add = new Array()
        this.maxSize = maxSize
        this.top = -1
    };

/**
 * @param {number} x
 * @return {void}
 */
CustomStack.prototype.push = function(x) {

    if (this.top < this.maxSize - 1) {
        ++this.top
        this.res[this.top] = x
        this.add[this.top] = 0
    }
};

/**
 * @return {number}
 */
CustomStack.prototype.pop = function() {
    if (this.top >= 0) {
        const item = this.res[this.top] + this.add[this.top]
        this.top--
        return item
    }
    return -1

};

/**
 * @param {number} k
 * @param {number} val
 * @return {void}
 */
CustomStack.prototype.increment = function(k, val) {
    for(let i = 0; i < Math.min(k, this.top+1); i++) {
        this.add[i] +=  val
    }
};

/**
 * Your CustomStack object will be instantiated and called as such:
 * var obj = new CustomStack(maxSize)
 * obj.push(x)
 * var param_2 = obj.pop()
 * obj.increment(k,val)
 */
```


####复杂度
* 时间复杂度 O(1)
* 空间复杂度 O(maxSize)



     
  
