
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 136 只出现一次的数字
Description
<pre>
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

示例1:
```base
输入: [2,2,1]
输出: 1
```
示例2:
```base
输入: [4,1,2,1,2]
输出: 4
</pre>

### 解题思路： 常规思路是：一个集合，记录数字出现的次数，大于1则从集合中删除，最后只剩一个，但使用了额外的看空间，不符合题意。该题主要考的是位运算相关的东西，异或。
* 自身异或得0 a ^ a = 0
* 异或0得自身 a ^ 0 = a
* 交换律 a ^ b ^ c = b ^ c ^ a

根据题目要求，线性复杂度的同时不使用额外空间，所以解答如下
```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    for(let i = 1; i < nums.length; i++) {
        nums[0] = nums[0] ^ nums[i]
    }
    return nums[0]
};
```
done~
