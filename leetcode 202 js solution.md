

# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 202. Happy Number
Description
<pre>
Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, 
replace the number by the sum of the squares of its digits, and repeat the process until the number
equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers
for which this process ends in 1 are happy numbers.

Example: 19 is a happy number

12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
</pre>

### 题目翻译： 写一个算法，判断一个数是否是 happy 的数。把一个数的每一位的平方相加，作为新的数字，循环，若得到最终结果为1，返回true，
或者陷入无限循环，返回false。
### 解题思路  
1. 新建一个对象，用于存放每次的结果，判断新得到的数是否存在对象里，若存在，则说明陷入死循环，返回false。若最终结果为1，退出循环，返回true。

solution:
```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
    var digit, result = n
    var theObj = {}
    while(result !== 1){
        result = 0
        while(n > 0){
            digit = n % 10
            result += Math.pow(digit, 2)
            n = (n - digit) / 10
        }
        if(!theObj[result]){
            theObj[result] = 1
            n = result
        } else {
            return false
        }
    }
    return true
};
```
Done.
