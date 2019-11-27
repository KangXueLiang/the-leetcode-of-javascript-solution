
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 1 Two Sum
Description
<pre>
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1]..
</pre>

### 题目翻译： 不解释
### 解题思路： 第一个数从前往后循环，第二个数从后往前循环，找出符合要求的两个数字。

solution: 
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    let i, j
    let len = nums.length
    for(i = 0; i < len; i++) {
        for(j = len - 1; j > i; j--){
            if(nums[i] + nums[j] === target){
                return [i, j]
            }
        }
    }
};
```
也可以用Map解答
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    let map = new Map()
    for (let i = 0; i < nums.length; i++) {
        let tmp = target - nums[i]
        if (map.has(tmp)) {
            return [map.get(tmp), i]
        }
        map.set(nums[i], i)
    }
    return []
};
```
也可以用hash解答
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    const hash = {};
    nums.forEach((num, idx) => hash[num] = idx)
    
    let result = [];
    for (let i=0; i < nums.length; i++) {
        let value = target - nums[i];
        if (hash[value]) {
            result = [i, hash[value]];
            break;
        }
    }
    return result;
};
```
方法太多了，Done.
