
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 190. Reverse Bits
Reverse bits of a given 32 bits unsigned integer.

For example, given input 43261596 (represented in binary as 00000010100101000001111010011100), return 964176192
(represented in binary as 00111001011110000010100101000000).

Follow up:
If this function is called many times, how would you optimize it?
</pre>

### 题目翻译： 求一个32位的十进制数字的二进制翻转后的十进制数字
### 解题思路： 貌似不用思路吧……

solution1:
```js
var reverseBits = function(n) {
    var res = 0;
    for(var i = 0; i< 32; i++){
        var bit = n &1;
        n >>=1;
       res = (res*2)+bit;
    }
    return res;
};
```
solution2: 
```js
var reverseBits = function(n) {
    var tmp = n.toString(2).split('').reverse()
    while(tmp.length < 32){
        tmp.push('0')
    }
    return parseInt(tmp.join(''), 2)
};
```
Done.
