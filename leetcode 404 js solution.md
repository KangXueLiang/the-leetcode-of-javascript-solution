

# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 404. Sum of Left Leaves
Description
<pre>
Find the sum of all left leaves in a given binary tree.

Example:

    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.
</pre>

### 题目翻译： 求 所有左叶的 值 的 和
### 解题思路  
1. 用一个闭包
2. 递归
3. 分析清楚如何把值加起来即可

slution:
<pre>
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var sumOfLeftLeaves = function(root) {
    var sum = 0
    function traverse(root){
    if(!root){
        return sum
    } else {
        if(root.left !== null){
            if(!root.left.left && !root.left.right){
                 sum = sum + root.left.val
            }
            
        }
        traverse(root.left)
        traverse(root.right)
    }
    return sum
    }
   traverse(root, sum)
    return sum
};
</pre>
Done.
