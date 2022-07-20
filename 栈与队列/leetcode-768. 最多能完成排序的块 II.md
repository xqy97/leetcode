## 题目描述
https://leetcode.cn/problems/max-chunks-to-make-sorted-ii/

## 解题思路
每块尽可能分小，后一块的数字必须比前一快的数字大，
因为有重复数字，所以重复数字可以单独分一块，
因为需要比较前后元素大小，所以联想到单调栈

## 单调递增栈

```javascript
for (遍历这个数组)
{
	if (栈空 || 栈顶元素大于等于当前比较元素) {
	    入栈;
	} else {
	    while (栈不为空 && 栈顶元素小于当前元素) {
                栈顶元素出栈;
                更新结果;
	    }
	    当前数据入栈;
	}
}
```

## 代码
```javascript
var maxChunksToSorted = function(arr) {
    let stack = []
    for(let i = 0; i < arr.length; i++) {
        if (!stack.length || arr[i] >= stack[stack.length - 1]) {
            stack.push(arr[i])
        } else {
            const last = stack.pop()
            while(stack[stack.length - 1] > arr[i]) {
                stack.pop()
            }
            stack.push(last)
        }
    }
    return stack.length
};
```

##复杂度
* 时间复杂度 O(n)
* 空间复杂度 O(n)
