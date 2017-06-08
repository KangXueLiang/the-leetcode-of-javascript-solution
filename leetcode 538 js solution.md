
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 538. Convert BST to Greater Tree
Description
<pre>
Given a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed
to the original key plus sum of all keys greater than the original key in BST.

Example:

Input: The root of a Binary Search Tree like this:
              5
            /   \
           2     13

Output: The root of a Greater Tree like this:
             18
            /   \
          20     13
</pre>

### 题目翻译：给一个BST，把它的每个节点的值转换为  所有比该节点值大(包括相等)的二叉树节点值 之和   
### 解题思路
1. 写一个函数，遍历二叉树，把所有二叉树的节点的值放入一个数组内
2. 分层遍历二叉树，把每个节点值与数组内元素比较，求大于该节点值的元素的和
3. 改变该节点值
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
 * @return {TreeNode}
 */
var convertBST = function(root) {
    if(!root){
        return null
    }
    var result = []
    result = traverse(root, result)
    var lr = result.length
    
    var row = [root]
    while(len = row.length){ // 分层遍历二叉树。
        for(var i = 0 ; i < len; i++){ //每一层的节点数循环
            var sum = 0
            for(var j = 0; j < lr; j++){ //数组循环，求sun，并替换节点值
                if(result[j] >= row[i].val){
                    sum += result[j]
                }
            }
            if(row[i].left !== null) row.push(row[i].left)
            if(row[i].right !== null) row.push(row[i].right)
            row[i].val = sum
        }
        row.splice(0,len)//  初始化row

    }
    return root
};
function traverse(root, result = []){ //遍历二叉树，把所有节点值push到数组内。
    if(!root){
        return result
    } else {
        result.push(root.val)
        traverse(root.left, result)
        traverse(root.right, result)
    }
    return result
}
</pre>
### 结果！！！AC了以后看别人的解题思路，发现自己简直就是个智障…………以下是别人的solution
<pre>
var convertBST = function(root) {
    var sum = 0;
    var convert = function(node) {
        if (!node) return;
        convert(node.right);
        node.val += sum;
        sum = node.val;
        convert(node.left);
    };
    convert(root);
    return root;
}
</pre>
Done.
