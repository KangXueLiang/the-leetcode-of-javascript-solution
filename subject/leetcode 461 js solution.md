
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 461. Hamming Distance
Description
<pre>
The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

Given two integers x and y, calculate the Hamming distance.

Note:
0 ≤ x, y < 231.

Example:

Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ?   ?

The above arrows point to positions where the corresponding bits are different.
</pre>

### 题目翻译： 给两个正整数，求出他们二进制表示位上的不同的个数。即（Hamming Distance）
### 解题思路： 按位异或，只有两个不同才为1，相同则为0.

solution: 
```js
/**
 * @param {number} x
 * @param {number} y
 * @return {number}
 */
var hammingDistance = function(x, y) {
    return (x ^ y).toString(2).replace(/0/g, '').length
};
```
Done.
