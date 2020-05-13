# Remove K Digits

###### tags: `LeetCode`

## 題目

Given a non-negative integer num represented as a string, remove k digits from the number so that the new number is the smallest possible.

**Example 1:**

    Input: num = "1432219", k = 3
    Output: "1219"
    Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.
    
**Example 2:**

    Input: num = "10200", k = 1
    Output: "200"
    Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.

**Example 3:**
    Input: num = "10", k = 2
    Output: "0"
    Explanation: Remove all the digits from the number and it is left with nothing which is 0.

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3328/)

## C++程式碼
```C++
class Solution {
public:
    string removeKdigits(string num, int k) {
        if(num.length()==k) return "0";
        while(k){
            int size = num.length();
            int index;
            
            //消去降序數列
            for(index=0; index<size-1; index++)
                if(num.at(index)>num.at(index+1)) {
                    num.erase(index, 1);
                    k--;
                    break;                    
                }
            
            //消去降序數列後，從右邊開始刪除k個值
            if(index==size-1){
                num.erase(num.length()-k,k);
                break;
            }
        }
        
        //消去開頭的0
        if(num.find_first_not_of("0")) num.erase(0, num.find_first_not_of("0"));
        
        if(num.length()==0) return "0";
            
        return num;       
    }
};

