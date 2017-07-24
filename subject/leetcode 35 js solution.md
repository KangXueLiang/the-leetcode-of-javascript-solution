# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 35. Search Insert Position
Description
<pre>
Given a sorted array and a target value, return the index if the target is found. If not, return the index where
it would be if it were inserted in order.

You may assume no duplicates in the array.

Here are few examples.
[1,3,5,6], 5 → 2
[1,3,5,6], 2 → 1
[1,3,5,6], 7 → 4
[1,3,5,6], 0 → 0
</pre>

### 题目翻译： 给一个已排好序的数组和一个目标值，如果目标值在数组内，返回该目标值的索引，否则，返回它插入数组中的索引。
### 解题思路： 运用indexOf()函数判断是否在数组内。然后遍历数组，找出它应该插入的位置。

slution: 
<pre>
var searchInsert = function(nums, target) {
    var len = nums.length
    var theIndex = nums.indexOf(target)
    if(theIndex !== -1){
        return theIndex
    } else {
        if(target > nums[len - 1]) return len
        for(var i = 0; i < len; i++){
            if(target < nums[i]){
                return i
            }
        }
        
    }
};
</pre>
这种解法的时间复杂度是O(n),也可以通过二分法实现复杂度O(log(n))
<pre>
var searchInsert = function(nums, target) {
    var low = 0, high = nums.length - 1
    while(low <= high){
        var mid = (low + high) / 2 | 0
        if(nums[mid] === target) return mid
        else if(nums[mid] > target) high = mid - 1
        else low = mid + 1
    }
    return low
};
</pre>
Done.
