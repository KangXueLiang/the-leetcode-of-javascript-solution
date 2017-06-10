# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 609. Find Duplicate File in System
Description
<pre>
Given a list of directory info including directory path, and all the files with contents in this directory, 
you need to find out all the groups of duplicate files in the file system in terms of their paths.

A group of duplicate files consists of at least two files that have exactly the same content.

A single directory info string in the input list has the following format:

"root/d1/d2/.../dm f1.txt(f1_content) f2.txt(f2_content) ... fn.txt(fn_content)"

It means there are n files (f1.txt, f2.txt ... fn.txt with content f1_content, f2_content ... fn_content, 
respectively) in directory root/d1/d2/.../dm. Note that n >= 1 and m >= 0. If m = 0, it means the directory 
is just the root directory.

The output is a list of group of duplicate file paths. For each group, it contains all the file paths of 
the files that have the same content. A file path is a string that has the following format:

"directory_path/file_name.txt"

Example 1:
Input:
["root/a 1.txt(abcd) 2.txt(efgh)", "root/c 3.txt(abcd)", "root/c/d 4.txt(efgh)", "root 4.txt(efgh)"]
Output:  
[["root/a/2.txt","root/c/d/4.txt","root/4.txt"],["root/a/1.txt","root/c/3.txt"]]
Note:
No order is required for the final output.
You may assume the directory name, file name and file content only has letters and digits, and the length 
of file content is in the range of [1,50].
The number of files given is in the range of [1,20000].
You may assume no files or directories share the same name in the same directory.
You may assume each given directory info represents a unique directory. Directory path and file info are 
separated by a single blank space.
Follow-up beyond contest:
Imagine you are given a real file system, how will you search files? DFS or BFS?
If the file content is very large (GB level), how will you modify your solution?
If you can only read the file by 1kb each time, how will you modify your solution?
What is the time complexity of your modified solution? What is the most time-consuming part and memory 
consuming part of it? How to optimize?
How to make sure the duplicated files you find are not false positive?
</pre>

### 题目翻译：额……太长了不想翻译
### 解题思路：题目意思很清楚，把重复内容的路径放到同一个数组的 子数组 内。
<pre>
slution:
/**
 * @param {string[]} paths
 * @return {string[][]}
 */
var findDuplicate = function(paths) {
   var tmp = []
   for(var i = 0; i < paths.length; i++){
       var curr = paths[i].split(" ")
       for(var j = 1; j < curr.length; j++){
           tmp.push(`${curr[0]}/${curr[j]}`)
       }
   } //把原数组中的 每一项 由 "root/a 1.txt(abcd) 2.txt(efgh)" -> "root/a/1.txt(abcd)", "root/a/2.txt(efgh)"
   var result = {}
   for(var k = 0; k < tmp.length; k++){
       tmp[k] = tmp[k].split("(")
       if(!result[tmp[k][1]]){
           result[tmp[k][1]] = [tmp[k][0]]
       } else {
           result[tmp[k][1]].push(tmp[k][0])
       }
   } /*新建一个对象， 把内容作为 属性名， 属性值为一个对象，具体形式为{ abcd): [root/a/1.txt], efgh): [root/a/2.txt]}，把同样内容的
   路径放到同一个数组内。*/
   var theEnd = []
   for(var key in result){
       if(result[key].length !== 1) theEnd.push(result[key])
   }  //遍历对象，把重复内容(即属性值 数组 的length > 1的 数组 push到一个新的数组内，即为所求结果)
   return theEnd 
   
};
</pre>
Done.
