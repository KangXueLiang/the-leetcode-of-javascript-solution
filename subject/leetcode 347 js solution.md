

# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 347. Top K Frequent Elements
Description
<pre>
Given a non-empty array of integers, return the k most frequent elements.

For example,
Given [1,1,1,2,2,3] and k = 2, return [1,2].

Note: 
You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
Your algorithm's time complexity must be better than O(n log n), where n is the array's size.
</pre>

### 题目翻译：给了一个非空正整数数组，返回其中出现次数最多的前k个数。要求时间复杂度为O(n * log n)
### 解题思路  
1. 新建对象，去重，并把元素与出现的次数对应起来。
2. 把对象的值（即元素出现的次数）作为一个新建数组的下标，把出现该次数的元素作为新建数组的子元素中，与下标相对应。
3. 从后向前遍历新建数组，即出现次数的由多到少的排序，拿出前k个元素，放到结果数组中。

solution:
```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    var tmp = []
    var obj = {}
    var len = nums.length
    var result = []
    for(var i = 0; i < len; i++){
        if(obj[nums[i]]) obj[nums[i]]++
        else obj[nums[i]] = 1
    }
    for(var key in obj){
        if(!tmp[obj[key]]) tmp[obj[key]] = []
        tmp[obj[key]].push(key)
    }
    for(var pos = tmp.length - 1; pos >= 0 && k > 0; pos--){
        if(tmp[pos]){
            for(var j = 0; j < tmp[pos].length; j++){
                result.push(parseInt(tmp[pos][j]))
                k--
            }
        }
    }
    return result
};
```
还有一种办法，用堆排序的，就不介绍了，繁琐，不过时间复杂度也正好满足。

Done.
