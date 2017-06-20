


# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 93. Restore IP Addresses
Description
<pre>
Given a string containing only digits, restore it by returning all possible valid IP address combinations.

For example:
Given "25525511135",

return ["255.255.11.135", "255.255.111.35"]. (Order does not matter)
</pre>

### 题目翻译：给一个字符串，输出由该字符串组成的正确的IP地址。
### 解题思路：
1. 回溯，深度优先。

slution:
<pre>
/**
 * @param {string} s
 * @return {string[]}
 */
 
var restoreIpAddresses = function(s) {
  return restore2(s)  
};
function restore2(s, part = [], result = []){//part表示当前暂存的IP
   if(s.length > 13){
       return []
   } 
   if(part.length == 3){//如果当前part已经进行到第四位，直接让后面的所有字符串进行判断是否为正确的IP地址，然后输出到结果数组或者break
       if(isIP(s)){
           part.push(s)
           result.push(part.join("."))
           part.pop()//丢掉最后一个值，进行回溯查找。
           return 
       } else {
           return 
       }
   }
   for(var i = 1; i < 4; i++){
       curr = s.substr(0, i)
       if(s === ""){
           break
       }else if(isIP(curr)){
           part.push(curr)
           restore2(s.substr(i), part, result)
       } else{
           break
       }
       part.pop()
   }
   return result
}
function isIP(value){ //判断一个值是否为正确的IP
    if(value === ""){
        return false
    }
    if(value === "0"){
        return true
    }
    if(value[0] ==="0" && value.length > 1){
        return false
    }
    return value < 256
}

</pre>
Done.
