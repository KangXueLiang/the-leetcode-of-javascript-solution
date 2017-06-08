# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 257. Binary Tree Paths
Description
<pre>
Given a binary tree, return all root-to-leaf paths.

For example, given the following binary tree:

   1
 /   \
2     3
 \
  5
All root-to-leaf paths are:

["1->2->5", "1->3"]
</pre>

### 题目翻译：给一个二叉树，返回一个从根到叶的路径的字符串为元素的数组。
### 解题思路：一开始没有思路，后来看了别人的JAVA的solution，才知道如何解答。
1. 因为考虑到用递归。思考递归的两个要点：一个是结束条件，一个是往结束条件推导的方法。
判断节点为叶时，退出递归。
每次递归需要把当前路径保存，最终的数组保存并递归下去。
2. 题目所给的函数参数不够，新建函数遍历二叉树。

slution:
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {string[]}
 */
var binaryTreePaths = function(root) {
    var result = []
    if(!root){
        return []
    } else {
        searchBT(root, "", result)
    }
    return result
};
function searchBT(root, path = "", result = []){ //新建函数遍历二叉树
    if(root.left == null && root.right == null){
        result.push(path + root.val) //如果当前节点为叶，把路径push到结果数组内。
    }
    if(root.left !== null){
        searchBT(root.left, path + root.val + "->", result) //如果左叶存在，递归，同时把路径扩展，并把表示结果的result空数组保存，传递。
    }
    if(root.right !== null){
        searchBT(root.right, path + root.val + "->", result) //同左叶
    }
}
</pre>
Done.
