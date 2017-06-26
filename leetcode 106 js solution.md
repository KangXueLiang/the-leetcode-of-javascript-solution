
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 106. Construct Binary Tree from Inorder and Postorder Traversal
Description
<pre>
Given inorder and postorder traversal of a tree, construct the binary tree.

Note:
You may assume that duplicates do not exist in the tree.
</pre>

### 题目翻译： 给一个二叉树的中序和后序遍历，求此二叉树的结构，注意：不考虑出现重复的节点
### 解题思路： 后序遍历最后一个节点总是根节点，然后在中序遍历中找到此节点，其左边为左枝，右边为右枝，再从后序遍历中把左枝的后序与右枝的后序找出来，递归。

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
 * @param {number[]} inorder
 * @param {number[]} postorder
 * @return {TreeNode}
 */
var buildTree = function(inorder, postorder) {
    if(inorder.length !== 0){
        var rootValue = postorder.pop()//后序遍历最后一个值为当前根节点的值
        var root = new TreeNode(rootValue)//构造根节点
        var inorderLeft = inorder.slice(0, inorder.indexOf(rootValue))//左枝的中序遍历
        var inorderRight = inorder.slice(inorder.indexOf(rootValue) + 1)//右枝的中序遍历
        
        var postorderLeft = postorder.slice(0, inorderLeft.length)//左枝的后序遍历
        var postorderRight = postorder.slice(inorderLeft.length)//右枝的后序遍历
        
        root.left = buildTree(inorderLeft, postorderLeft)
        root.right = buildTree(inorderRight, postorderRight)
    } else {
        return null
    }
    return root
};
```
Done.
