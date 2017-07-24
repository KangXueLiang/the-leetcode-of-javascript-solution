

# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 109. Convert Sorted List to Binary Search Tree
Description
<pre>
Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.
</pre>

### 题目翻译：给一个单向链表并且value值是升序排列的，把它转化成一个高度平衡的BST。
### 解题思路：我的方法是先把链表转成升序数组，再把数组转成二叉树。可能有点啰嗦，后面有简单防范，直接操作链表的。


solution1:
```js
var sortedListToBST = function(head) {
    return array2BST(linked2Array(head))
};
function linked2Array(head, result = []){ //把链表转成数组
  while(true){
        if(!head){
            break
        } else {
            result.push(head.val)
            head = head.next
        }
    }
    return result
}
function array2BST(array, root = new TreeNode()){//把数组转成二叉树
    if(!array.length){
        return null
    } else{
        var mid = array.length / 2 | 0
        root.val = array[mid]
        root.left = array2BST(array.slice(0, mid))
        root.right = array2BST(array.slice(mid + 1))
    }
    return root
}
```
solution2 
```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {TreeNode}
 */
var sortedListToBST = function(head, tail) {
    if(!head) return null;
    var slow = head, fast = head;
    while(fast != tail){
        fast = fast.next;
        if(fast != tail){
            fast = fast.next;
            slow = slow.next;
        }
    }
    var node = new TreeNode(slow.val);
    node.left = head == slow ? null : sortedListToBST(head, slow);
    node.right = slow.next == tail ? null : sortedListToBST(slow.next, tail);
    return node;
};

```
Done.
