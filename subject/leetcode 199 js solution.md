# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 199. Binary Tree Right Side View
Description
<pre>
Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes
you can see ordered from top to bottom.

For example:
Given the following binary tree,
   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---
You should return [1, 3, 4].
</pre>

### 题目翻译： 给一个二叉树，假设你站在二叉树的右边，输出你能看到的节点的值组成的数组。
### 解题思路：求二叉树每一层的最右边的节点的值。
1. 按层遍历，把每一层的节点的值放入一个数组内
2. 把数组的最后一个元素输出到 结果数组内

solution:
```js
var rightSideView = function(root) {
    var row = [root]
    var tmp = []
    var result = []
    while(len = row.length){
        for(var i = 0; i < len ; i++){
            if(!row[i]){
                return []
            } else{
                tmp.push(row[i].val)
                if(row[i].left !== null) row.push(row[i].left)
                if(row[i].right !== null) row.push(row[i].right)
            }
        }
        result.push(tmp[tmp.length - 1])
        row.splice(0, len)
        tmp = []
    }
    return result
};
```
Done.
