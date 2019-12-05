
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 1 两数相加
给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

示例：

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807

</pre>

### 解题思路： val相加，获取余数，递归求解

solution: 
```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
 function addTwoNumbers (l1, l2, carry = 0){
     let v = l1.val + l2.val + carry
     c = v > 9 ? 1 : 0
     v = v % 10
     return {
         val: v,
         next: l1.next || l2.next || c 
               ? addTwoNumbers(
                    l1.next || new ListNode(0),
                    l2.next || new ListNode(0),
                    c
               )
               : null
     }
 }
```

### 解题思路2： 官方解释。先创建一个哑节点，当前指针指向该节点，然后用p、q指向当前链表节点。将两个链表节点都为空作为终止循环的条件，模拟运算后，指针后移，最后判断当前进位，如果为1,说明链表需要加深一层，最后返回哑结点的next，即我们最终需要的链表。
```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
function addTwoNumbers (l1, l2) {
     let p = l1, q  = l2, carry = 0
     let dummyHead = new ListNode(0)
     let curr = dummyHead
     while(p != null || q != null) {
         let v1 = p ? p.val : 0
         let v2 = q ? q.val : 0
         let sum = v1 + v2 + carry
         if (sum > 9) {
            carry = 1
            sum = sum % 10
         } else {
            carry = 0
         }
         curr.next = new ListNode(sum)
         curr = curr.next
         p = p ? p.next : null
         q = q ? q.next : null
     }
     if (carry === 1) {
         curr.next = new ListNode(1)
     }
     return dummyHead.next
 }
 
```
复杂度分析

* 时间复杂度：O(max(m,n))，假设 m 和 n 分别表示 l1 和 l2 的长度，上面的算法最多重复 max(m,n) 次。

* 空间复杂度：O(max(m,n))， 新列表的长度最多为 max(m,n)+1。

Done.
