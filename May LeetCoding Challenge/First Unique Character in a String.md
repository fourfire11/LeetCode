# First Unique Character in a String

###### tags: `LeetCode`

## 題目
Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

**Examples**
    
    s = "leetcode"
    return 0.

    s = "loveleetcode",
    return 2.
    
:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3320/)

## C++程式碼
```C++
class Solution {
public:
    int firstUniqChar(string s) {
        map<char, int> m;
        for(int i=0; i<s.length(); i++){
            m[s.at(i)]++;
        }
        for(int i=0; i<s.length(); i++){
            if(m[s.at(i)]==1) return i;
        }
        return -1;
    }
};