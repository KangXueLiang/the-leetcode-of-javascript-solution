# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 137. Single Number II
Description
<pre>
Given an array of integers, every element appears three times except for one, which appears exactly once. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?
</pre>

### 题目翻译： 给一个有整数组成的数组，每个数字都出现三次，只有一个出现了一次，找出这个数字。要求线性时间复杂度并且不能用额外内存。
### 解题思路： 我的想法是首先不能用额外空间，就要求不能创建新的数组或其他东西，只能原地修改数组。然后还要让原数组保持自己原有的数字，所以将
数组的每一项当成索引，然后把数组该索引的值进行修改，最后再循环一次，找到只修改了一次的那个索引。就是要求的那个值。

solution: 
```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    //如果只有一项，返回该项
    if(nums.length === 1){
        return nums[0]
    }
    let len = nums.length
    //循环一次，修改数组
    for(let i = 0; i < len; i++){
        var value = parseInt(nums[i])
        if(nums[value] != undefined){
            nums[value]+='One'
        }else{
            nums[value] = '0One'
        } 
    }
    //再次循环，找出出现单词的值。因为数组中可能有负值存在，而数组的负索引无法用常规遍历，所以用了for in 循环。
    for(var j in nums){
        if(nums[j] === parseInt(nums[j]) + 'One'){
            return +j
        }
    }
    return 0
};
```
Done.
### 总结： 提交之后发现耗时比较长，发现排名靠前的答案都是用位运算做的……因为对位运算不是很精通，就不贴了。
