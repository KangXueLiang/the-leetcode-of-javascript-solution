

# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 415. Add Strings
Description
<pre>
Given two non-negative integers num1 and num2 represented as string, return the sum of num1 and num2.

Note:

The length of both num1 and num2 is < 5100.
Both num1 and num2 contains only digits 0-9.
Both num1 and num2 does not contain any leading zero.
You must not use any built-in BigInteger library or convert the inputs to integer directly.
</pre>

### 题目翻译： 求两个字符串形式  非负整数  的和，结果也是字符串
### 题目要求：不能用系统内置的将字符串转为数字的函数。
### 解题思路  
1. 首先判断出两个字符串的长度，因为加法最多能进一，所以把较长字段前加一个0，较短字段前面加0直到两个字符串长度相当。
2. 从末尾开始提取字符串，相加。针对结果与进位相加 与 10 的比较，进行不同的操作。
3. 把结果前面多余的 0 去掉。

slution:
<pre>
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var addStrings = function(num1, num2) {
   var len = num1.length > num2.length ? num1.length : num2.length
   while(num1.length < len + 1){
       num1 = "0" + num1
   }
   while(num2.length <  len + 1){
       num2 = "0" + num2
   }
   var result = "", curr = 0, next = 0
   for(var i = len ; i >= 0; i--){
       var tmp = (+num1[i]) + (+num2[i])
       if((tmp + curr) >= 10){
           tmp = (tmp + curr) % 10
           next = 1
       } else {
           tmp = tmp + curr
           next = 0
       }
       result = tmp + result
       curr = next
   }
   while(result[0] == 0 && result.length !== 1){
       result = result.substr(1)
   }
   return result
};
</pre>
Done.
