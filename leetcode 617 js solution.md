# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 617. Merge Two Binary Trees
Description
<pre>
Given two binary trees and imagine that when you put one of them to cover the other, some nodes
of the two trees are overlapped while the others are not.

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then
sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

Example 1:
Input: 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
Output: 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
Note: The merging process must start from the root nodes of both trees.
</pre>

### 题目翻译： 把两个二叉树进行合并，节点的值为两个树同一位置节点值之和。
### 解题思路：递归，分情况遍历


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
 * @param {TreeNode} t1
 * @param {TreeNode} t2
 * @return {TreeNode}
 */
var mergeTrees = function(t1, t2) {
    if(t1 !== null && t2 !== null){
        t1.val += t2.val
        if(t1.left !== null && t2.left !== null){
            mergeTrees(t1.left, t2.left)
        }else if(!t1.left && t2.left !== null ){
            t1.left = t2.left
        }
        if(t1.right !== null && t2.right !== null){
            mergeTrees(t1.right, t2.right)
        }else if(!t1.right && t2.right !== null ){
            t1.right = t2.right
        }
    } else if(!t1 && t2!== null){
        t1 = t2
    }
    return t1
};
</pre>
Done.
