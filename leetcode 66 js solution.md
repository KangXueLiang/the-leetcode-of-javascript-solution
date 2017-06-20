

# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 66. Plus One
Description
<pre>
Given a non-negative integer represented as a non-empty array of digits, plus one to the integer.

You may assume the integer do not contain any leading zero, except the number 0 itself.

The digits are stored such that the most significant digit is at the head of the list.
</pre>

### 题目翻译：给一个表示数字的数组加一
### 解题思路：因为是加一，从后向前循环，只考虑每一位加1 % 10后是否为0，如果不是，直接break，表示不用进位。如果最高为为0，则数组前加一个为1的元素。


slution1:
<pre>
var plusOne = function(digits) {
    var len = digits.length
    for(var i = len - 1; i >= 0; i--){
        digits[i] = (digits[i] + 1) % 10
        if(digits[i] !== 0 && i !== 0){
            break
        }
        if(digits[i] === 0 && i === 0){
            digits.unshift(1)
        } 
    }
    return digits
}
</pre>
Done.
