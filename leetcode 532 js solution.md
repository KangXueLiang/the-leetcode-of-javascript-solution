# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 532. K-diff Pairs in an Array
Description
<pre>
Given an array of integers and an integer k, you need to find the number of unique k-diff
pairs in the array. Here a k-diff pair is defined as an integer pair (i, j), where i and
j are both numbers in the array and their absolute difference is k.

Example 1:
Input: [3, 1, 4, 1, 5], k = 2
Output: 2
Explanation: There are two 2-diff pairs in the array, (1, 3) and (3, 5).
Although we have two 1s in the input, we should only return the number of unique pairs.
Example 2:
Input:[1, 2, 3, 4, 5], k = 1
Output: 4
Explanation: There are four 1-diff pairs in the array, (1, 2), (2, 3), (3, 4) and (4, 5).
Example 3:
Input: [1, 3, 1, 5, 4], k = 0
Output: 1
Explanation: There is one 0-diff pair in the array, (1, 1).
Note:
The pairs (i, j) and (j, i) count as the same pair.
The length of the array won't exceed 10,000.
All the integers in the given input belong to the range: [-1e7, 1e7].
</pre>

### 题目翻译： 给一个数组，一个差值k,返回 数组中所有差值为k的一对儿元素的对数
### 解题思路：
1. 根据数组新建一个对象，属性名为数组元素，属性值为该元素出现的次数。
2. 分情况分析，如果k为0，则找出对象中属性值大于等于2的属性个数即可。如果k>0,则把 属性值+k 作为新的属性值 ，如果该对象有此属性，则说明原数组
存在差值为k的一对儿元素。

slution:
<pre>
var findPairs = function(nums, k) {
   if(nums.length === 0 || k < 0){
       return 0
   } 
   var theMap = {}
   var count = 0 
   for(var i = 0 ; i < nums.length; i++){
       theMap[nums[i]] === undefined ? theMap[nums[i]] = 1 :  theMap[nums[i]]++
   }
   if(k === 0){
       for(var key in theMap){
           if(theMap[key] >= 2){
               count++
           }
       }
   } else {
       for(key in theMap){
           if(theMap[parseInt(key) + k] !== undefined){
               count++
           }
       }
   }
   return count
};
</pre>
Done.
