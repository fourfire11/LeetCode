# Number Complement

###### tags: `LeetCode`

## 題目
Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

**Example 1:**

    Input: 5
    Output: 2
    Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
**Example 2:**

    Input: 1
    Output: 0
    Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3319/)

## C++程式碼
```C++
class Solution {
public:
    int findComplement(int num) {
        long long pow=1;
        long long comNum=0;
        do{ 
            if(num%2==0) comNum+=pow;
            num = (num >> 1);
            pow*=2;
        }while(num);
        
        return comNum;
    }
};