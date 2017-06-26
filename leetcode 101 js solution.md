
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 101. Symmetric Tree
<pre>
Description
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree [1,2,2,3,4,4,3] is symmetric:

    1
   / \
  2   2
 / \ / \
3  4 4  3
But the following [1,2,2,null,3,null,3] is not:
    1
   / \
  2   2
   \   \
   3    3
Note:
Bonus points if you could solve it both recursively and iteratively.
</pre>

### 题目翻译：镜像二叉树  判断一个二叉树是否左右对称。可以用递归和迭代解答。
### 解题思路
1. 写一个函数，把函数某一枝进行翻转
2. 写一个函数，判断两个二叉树是否深度相等。
3. 带入原函数

solution:
```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function(root) {
   if(!root){
       return true
   } else {
       var left = traverse(root.left)
       return (isEqual(left, root.right))
   }
};
function traverse(root){  //左右翻转一个二叉树
    if(!root){
        return null
    } else {
        var left = traverse(root.left)
        var right = traverse(root.right)
        root.left = right
        root.right = left
    }
    return root
}
function isEqual(p, q){  //判断两个二叉树是否完全一致。
    if(!q && !p){
    if(!q && !p){
    if(!q && !p){
        return true
    } else if(q && p){
        return p.val === q.val && isEqual(p.left, q.left) && isEqual(p.right, q.right)
    } else {
        return false
    }
    
}
```
Done.
