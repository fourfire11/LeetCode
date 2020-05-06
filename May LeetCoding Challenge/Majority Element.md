# Majority Element

###### tags: `LeetCode`

## 題目
Given an array of size n, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

**Example 1:**

    Input: [3,2,3]
    Output: 3

**Example 2:**

    Input: [2,2,1,1,1,2,2]
    Output: 2

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3321/)

## C++程式碼
```C++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        map<int, int> m;
        
        for(int i=0; i<nums.size(); i++){
            m[nums[i]]++;
            if (m[nums[i]] > nums.size()/2) return nums[i];
        }
        return -1;
    }
};