# Cousins in Binary Tree

###### tags: `LeetCode`

## 題目
In a binary tree, the root node is at depth `0`, and children of each depth `k` node are at depth `k+1`.

Two nodes of a binary tree are cousins if they have the same depth, but have **different parents**.

We are given the `root` of a binary tree with unique values, and the values `x` and `y` of two different nodes in the tree.

Return `true` if and only if the nodes corresponding to the values `x` and `y` are cousins.

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/02/12/q1248-01.png)


    Input: root = [1,2,3,4], x = 4, y = 3
    Output: false

**Example 2:**

![](https://assets.leetcode.com/uploads/2019/02/12/q1248-02.png)


    Input: root = [1,2,3,null,4,null,5], x = 5, y = 4
    Output: true
    
**Example 3:**

![](https://assets.leetcode.com/uploads/2019/02/13/q1248-03.png)


    Input: root = [1,2,3,null,4], x = 2, y = 3
    Output: false

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3322/)


## C++程式碼
```C++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    pair<int,int> DFS(TreeNode* curNode, int target, int depth, int parentVal){
        pair<int, int> l, r;
        if(curNode==NULL) return{-1,-1};
        cout << curNode->val << depth << parentVal << '\n';
        if(curNode->val==target) {cout << "hi"; return {depth, parentVal};}
        else{
            parentVal = curNode->val;
            l=DFS(curNode->left, target, depth+1, parentVal);
            r=DFS(curNode->right, target, depth+1, parentVal);
            
            if(r.first==-1) return l;
            else return r;
        }
    }
    
    bool isCousins(TreeNode* root, int x, int y) {
        pair<int, int> X, Y;
        if((x==1)||(y==1)) return false;
        else{
            X = DFS(root, x, 0, -1);
            cout << X.first << ' ' << X.second << '\n';
            Y = DFS(root, y, 0, -1);
            cout << Y.first << ' ' << Y.second << '\n';
            if((X.first==Y.first) && (X.second!=Y.second)) return 1;
        }
        
        return 0;
    }
};
