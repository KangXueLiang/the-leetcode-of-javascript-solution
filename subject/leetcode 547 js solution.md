
# the-leetcode-of-javascript-solution
用js刷leetcode时的一些想法及解题思路

## 547. Friend Circles
There are N students in a class. Some of them are friends, while some are not. Their friendship is transitive in nature. For example, if A is a direct friend of B, and B is a direct friend of C, then A is an indirect friend of C. And we defined a friend circle is a group of students who are direct or indirect friends.

Given a N*N matrix M representing the friend relationship between students in the class. If M[i][j] = 1, then the ith and jth students are direct friends with each other, otherwise not. And you have to output the total number of friend circles among all the students.

Example 1:
Input: 
[[1,1,0],
 [1,1,0],
 [0,0,1]]
Output: 2
Explanation:The 0th and 1st students are direct friends, so they are in a friend circle. 
The 2nd student himself is in a friend circle. So return 2.
Example 2:
Input: 
[[1,1,0],
 [1,1,1],
 [0,1,1]]
Output: 1
Explanation:The 0th and 1st students are direct friends, the 1st and 2nd students are direct friends, 
so the 0th and 2nd students are indirect friends. All of them are in the same friend circle, so return 1.
Note:
N is in range [1,200].
M[i][i] = 1 for all students.
If M[i][j] = 1, then M[j][i] = 1.

### 题目翻译： 一个班有N个同学，其中一些是朋友。假如A与B是朋友，B与C是朋友，那么A和C也是间接的朋友。我们就假设一个朋友圈就是那些直接或者间接朋友的集合。给出了一个N*N的矩阵M表示班里同学的关系。如果M[i][j] = 1, 那么第I个同学与第[j]个同学就是直接的朋友，否则不是。你需要输出所有的同学里有多少个朋友圈。
### 解题思路： 用并查集。

solution: 
```js
/**
 * @param {number[][]} M
 * @return {number}
 */

var findCircleNum = function(M) {
    var len = M.length
    if(len === 0){
        return 0
    }
    var a = new Uset(len)
    for(var i = 0; i < len; i++){
        for(var j = 0; j < M[i].length; j++){
            if(M[i][j] === 1){
              a.union(i,j)  
            }          
        }
    }
    return a.sets()
};


//实现一个并查集
class Uset{
    constructor(n){
        this.set = new Array(n).fill(-1)
    }
    
    //找出X所在集合的代表元素并做路径压缩
    find(x){
       if(this.set[x] < 0) {
           return x
       } else{
           return this.set[x] = this.find(this.set[x])
       }
    }
    
    //合并x和y所在集合
    //返回this
    union(x,y){
        var xset = this.find(x)
        var yset = this.find(y)
        //相同集合里什么也不做
        if(xset === yset){
            return this
        } else { //不同集合里合并
            if(this.set[xset] < this.set[yset]){
                this.set[xset] -= this.set[yset]
                this.set[yset] = xset
            } else if(this.set[xset] > this.set[yset]){
                this.set[yset] -= this.set[xset]
                this.set[xset] = yset
            } else{
                this.set[xset]--
                this.set[yset] = xset
            }
            return this
        }
    }   
    //判断x和y是否在同一集合里
    same(x,y){
        return this.find(x) === this.find(y)
    }
    sets(){
        return this.set.filter(it => it < 0).length
    }
}
```
Done.
