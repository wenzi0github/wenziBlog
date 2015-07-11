leetcode-rotate-array，文章地址：[http://www.xiabingbao.com/algorithm/2015/04/19/leetcode-rotate-array](http://www.xiabingbao.com/algorithm/2015/04/19/leetcode-rotate-array/)

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
    var len, after;
    len = nums.length;
    k = k%len;
    after = nums.splice(-k, k); // 得到最后k个元素
    for(var i=k-1; i>=0 ;i--){
        nums.unshift(after[i]); // 填充到数组的开始位置
    }
};
```
