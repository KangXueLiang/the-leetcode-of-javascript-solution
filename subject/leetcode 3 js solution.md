
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 3 无重复字符的最长子串
Description
<pre>
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

示例 1:

输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
示例 2:

输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
示例 3:

输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-substring-without-repeating-characters
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
</pre>

### 题目翻译： 不解释
### 解题思路： 第一个数从前往后循环，第二个数从后往前循环，找出符合要求的两个数字。

solution: 
```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    if (s.length === 0) return 0
    let i = 0, j = 1
    let curr = 1, max = 1
    let len = s.length
    let m = new Map()
    m.set(s[0], 0)
    while(j < len) {
        if (m.has(s[j]) && m.get(s[j]) >= i) {
            i = m.get(s[j]) + 1
            curr = j - i + 1
        } else {
            curr++
            max = Math.max(max, curr)
        }
        m.set(s[j], j)
        j++
    }
    return max
};
```
Done.
