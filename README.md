# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 235. Lowest Common Ancestor of a Binary Search Tree
Description
<pre>
Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes
v and w as the lowest node in T that has both v and w as descendants (where we allow a node to be a 
descendant of itself).”

        _______6______
       /              \
    ___2__          ___8__
   /      \        /      \
   0      _4       7       9
         /  \
         3   5
For example, the lowest common ancestor (LCA) of nodes 2 and 8 is 6. Another example is LCA of nodes
2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
</pre>

### 解题思路：这道题是求任意某两个节点的共同的最小祖先节点。
1. 给的二叉树是一个BST
2. 因为是求祖先节点，所有给的两个节点的value与最小的value值相差之积必为负数，作为循环结束条件。
3. 改变当前root的指向，并分析祖先元素处于当前root的左枝or右枝
4. 返回root

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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */

var lowestCommonAncestor = function(root, p, q) {
    while((root.val - p.val) * (root.val - q.val) > 0){
        root = root.val > p.val ? root.left : root.right
    }
    return root
};
</pre>
Done.
