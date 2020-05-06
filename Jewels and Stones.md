# Jewels and Stones

###### tags: `LeetCode`

## 題目
You're given strings `J` representing the types of stones that are jewels, and `S` representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in `J` are guaranteed distinct, and all characters in `J` and `S` are letters. Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.

:::info
**Example 1:** 
**Input**: J = "aA", S = "aAAbbbb"
**Output**: 3
:::

:::info
**Example 2:** 
**Input**: J = "z", S = "ZZ"
**Output**: 0
:::

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3317/)

## 解題方法
- find_first_of 函數介紹

## C++程式碼
```C++
class Solution {
public:
    int numJewelsInStones(string J, string S) {
        int index=S.find_first_of(J);
        int count=0;

        while(index!=-1){
            index = S.find_first_of(J,index+1);
            count++;
        }
        return count;
    }
};