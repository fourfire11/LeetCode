#  Permutation in String

###### tags: `LeetCode`

## 題目

Given two strings **s1** and **s2**, write a function to return true if **s2** contains the permutation of **s1**. In other words, one of the first string's permutations is the **substring** of the second string.

**Example 1:**

    Input: s1 = "ab" s2 = "eidbaooo"
    Output: True
    
Explanation: s2 contains one permutation of s1 ("ba").
    
**Example 2:**

    Input:s1= "ab" s2 = "eidboaoo"
    Output: False

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3333/)

## C++程式碼
```C++
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        map<char, int> m1, m2;
        int L1=s1.length(), L2=s2.length();
        bool isEqual;
        
        for(char c:s1) m1[c]++;
        
        for(int i=0; i<L2; i++){
            isEqual = true;
            m2[s2.at(i)]++;
    
            if(i >= L1-1){ 
                int startIndex = i-L1+1;
                for(pair p:m1) 
                    if(m2[p.first] != p.second) {isEqual = false; break;}
                if(isEqual) return true;

                m2[s2.at(startIndex)]--;
            }
        }
        
        return false;
    }
};
