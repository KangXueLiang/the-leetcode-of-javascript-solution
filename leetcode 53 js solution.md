# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 53. Maximum Subarray
Description
<pre>
Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array [-2,1,-3,4,-1,2,1,-5,4],
the contiguous subarray [4,-1,2,1] has the largest sum = 6.
</pre>

### 题目翻译： 给一个数组，求出连续元素组成的子数组的最大的和。
### 解题思路：
1. 定义变量，当前和  sum    最大和   max， 初始值均为数组第一项
2. 循环数组，比较 当前和 加上 当前元素 的和 与 当前元素 的大小，并把其中较大值 赋值给  当前和
3. 比较当前和与最大和，把较大值 赋值 给最大和
4. 返回 最大和。

slution:
<pre>
var maxSubArray = function(nums) {
    var max = nums[0]
    var sum = nums[0]
    for(var i = 1; i < nums.length; i++){
        sum = Math.max(sum + nums[i], nums[i])
        max = Math.max(max, sum)
    }
    return max
};
</pre>
Done.
