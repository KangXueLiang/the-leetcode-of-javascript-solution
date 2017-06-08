
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 515. Find Largest Value in Each Tree Row
Description
<pre>
You need to find the largest value in each row of a binary tree.
Example:
Input: 

          1
         / \
        3   2
       / \   \  
      5   3   9 

Output: [1, 3, 9]
</pre>

### 题目翻译：求二叉树的每一层的最大数，并返回一个包括这些最大数的数组。
### 解题思路：
1. 按层循环，把每一层的节点的value都放到一个二维数组里，
2. 求这个数组每个子数组的最大值


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
 * @return {number[]}
 */
var largestValues = function(root) {
    if(!root){
        return []
    }
    var row = [root]
    var result = []
    var tmp = [] 
    while(len = row.length){
        for(var i = 0; i < len; i++){
            tmp.push(row[i].val)
            if(row[i].left) row.push(row[i].left)
            if(row[i].right) row.push(row[i].right)        
        }
        row.splice(0,len)
        result.push(tmp)
        tmp = []
    }
    var ls = result.length
    for(var j = 0; j < ls; j++){
        result[j] = Math.max(...result[j])
    }
    return result
};
</pre>
Done.
