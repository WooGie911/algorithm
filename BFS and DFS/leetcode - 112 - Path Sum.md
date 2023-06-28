# 112. Path Sum

## 문제 :

Given the root of a binary tree and an integer targetSum, return true if the tree has a root-to-leaf path such that adding up all the values along the path equals targetSum.

A leaf is a node with no children.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src = 'https://assets.leetcode.com/uploads/2021/01/18/pathsum1.jpg'>

<br/>

Input: root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22
<br/>
Output: true
<br/>
Explanation: The root-to-leaf path with the target sum is shown.

<br/>

### Example 2:

<img src = 'https://assets.leetcode.com/uploads/2021/01/18/pathsum2.jpg'>

<br/>

Input: root = [1,2,3], targetSum = 5
<br/>
Output: false
<br/>
Explanation: There two root-to-leaf paths in the tree:
<br/>
(1 --> 2): The sum is 3.
<br/>
(1 --> 3): The sum is 4.
<br/>
There is no root-to-leaf path with sum = 5.

<br/>

### Example 3:

Input: root = [], targetSum = 0
<br/>
Output: false
<br/>
Explanation: Since the tree is empty, there are no root-to-leaf paths.

<br/>

---

## 조건

### Constraints:

- The number of nodes in the tree is in the range [0, 5000].
- -1000 <= Node.val <= 1000
- -1000 <= targetSum <= 1000

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} targetSum
 * @return {boolean}
 */
var hasPathSum = function(root, targetSum) {

    let output = false;

    const loop = (tree,value)=>{

        if(tree?.val || tree?.val === 0){
            tree.val += value
        }

        if(!tree?.left && !tree?.right &&tree?.val === targetSum){
            output = true
        }

        if(tree?.left){
            loop(tree.left,tree.val)
        }

        if(tree?.right){
            loop(tree.right,tree.val)
        }
    }

    loop(root,0)

    return output
};
```
