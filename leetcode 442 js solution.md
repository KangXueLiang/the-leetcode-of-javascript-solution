# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 442. Find All Duplicates in an Array
Description
<pre>
Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements that appear twice in this array.

Could you do it without extra space and in O(n) runtime?

Example:
Input:
[4,3,2,7,8,2,3,1]

Output:
[2,3]
</pre>

### 题目翻译： 给定一个数组，求出其中的重复项。要求：不能创建额外空间，时间复杂度为O(n)
### 解题思路：把数组每一个元素的绝对值作为一个新的下标，把新下标所指向的元素乘以 -1， 遍历数组时，如果当前元素为负，那么他的下标就是重复项。

slution:
<pre>
var findDuplicates = function(nums) {
    var len = nums.length
    var result = []
    for(var i = 0; i < len; i++) {
        if(nums[Math.abs(nums[i]) - 1] < 0){
            result.push(Math.abs(nums[i]))
        }
        nums[Math.abs(nums[i]) - 1] =  nums[Math.abs(nums[i]) - 1] * (-1)
    }
    return result
};
</pre>
Done.
