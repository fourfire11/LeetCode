# Jewels and Stones

###### tags: `LeetCode`

## 題目
You're given strings `J` representing the types of stones that are jewels, and `S` representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in `J` are guaranteed distinct, and all characters in `J` and `S` are letters. Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.


**Example 1:** 

    Input: 
    J = "aA", S = "aAAbbbb"

    Output:
    3

**Example 2:** 

    Input:
    J = "z", S = "ZZ"

    Output: 
    0

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3317/)

## 解題函數介紹
- s.find_first_of(string str)

回傳string s中，第一個出現「含有」string str中任一char的index值
- s.find_first_of(string str, int index)

回傳string s中，從位置index+1開始第一個出現「含有」string str中任一char的index值

### 其他相似函數
- s.find_last_of(string str) 

回傳**最後一個**出現str中任一char的index值
- s.find_fitst_not_of(string str)

回傳第一個**不屬於**str中任一char的index值
- s.find_last_not_of(string str)

回傳最後一個**不屬於**str中任一char的index值

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
