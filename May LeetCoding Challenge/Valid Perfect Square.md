# Valid Perfect Square

###### tags: `LeetCode`

## 題目

Given a positive integer num, write a function which returns True if num is a perfect square else False.

**Note: Do not** use any built-in library function such as `sqrt`.

**Example 1:**

    Input: 16
    Output: true

**Example 2:**

    Input: 14
    Output: false

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3324/)

## C++程式碼
```C++
class Solution {
public:
    bool isPerfectSquare(int num) {
        long long sq=1;
        while(sq*sq<num) sq++;
        if(sq*sq==num) return true;
        else return false;
    }
};
