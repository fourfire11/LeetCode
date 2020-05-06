# Ransom Note

###### tags: `LeetCode`

## 題目
Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

**Note:**
You may assume that both strings contain only lowercase letters.

    canConstruct("a", "b") -> false
    canConstruct("aa", "ab") -> false
    canConstruct("aa", "aab") -> true

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3318/)

## C++程式碼
```C++
class Solution {
public:
    bool canConstruct(string ransomNote, string magazine) {
        int findID;
        bool isFind = false;
        
        for(int i=0; i<ransomNote.length(); i++){
            findID=magazine.find(ransomNote.at(i));
            if(findID>magazine.length()) return false;
            magazine.replace(findID, 1, "");
        }
        return true;
    }
};