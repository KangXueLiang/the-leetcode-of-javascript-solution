# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 191. Number of 1 Bits
Description
<pre>
Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).

For example, the 32-bit integer ’11' has binary representation 00000000000000000000000000001011, so the function should return 3.
</pre>

### 题目翻译： 给一个数字，求出它的二进制数含有的1的个数
### 解题思路： Easy

slution: 暴力转换
<pre>
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
    var count = 0
    var result = (+n).toString(2).split("").map(function(n){
        if(n === "1"){
            count++
        }
    })
    return count
};
</pre>
solution2: 位运算 n & (n - 1) 得出一个比n二进制少一个1的数
<pre>
var hammingWeight = function(n) {
    var count = 0;
    while(n){
        n = n & (n-1);
        count++;
    }
    return count;
};
</pre>
Done.
