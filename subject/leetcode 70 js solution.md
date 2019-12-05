
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 1 爬楼梯
假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

示例 1：

输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
示例 2：

输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶

</pre>

### 解题思路： 斐波那契数列问题。n(1) = 1, n(2) = 2, n(3) = n(1) + n(2), n(4) = n(3) + n(2)...,所有的值都存在数组内

solution: 
```js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
    let result = [0, 1, 2]
    let s = 3
    if (n <= 2) {
        return result[n]
    } else {
        while( s <= n) {
            result[s] = result[s - 1] + result[s - 2]
            s++
        }
        return result[n]
    } 
};
```
Done.
