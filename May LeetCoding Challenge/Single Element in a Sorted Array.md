# Single Element in a Sorted Array

###### tags: `LeetCode`

## 題目

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once. Find this single element that appears only once.

**Example 1:**

    Input: [1,1,2,3,3,4,4,8,8]
    Output: 2
    
**Example 2:**

    Input: [3,3,7,7,10,11,11]
    Output: 10

**Note:** Your solution should run in O(log n) time and O(1) space.

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3327/)

## C++程式碼
```C++
class Solution {
public:
    int check(vector<int>& nums, int l, int r, int mid){
        int key;
        if((mid==l)||(mid==r)) return nums[mid];
        if(r-l==2) if(nums[r]==nums[mid]) return nums[l]; else return nums[r];
        if((nums[mid]!=nums[mid-1])&&(nums[mid]!=nums[mid+1])) return nums[mid];
        if(((mid%2==1) && (nums[mid]==nums[mid-1])) || ((mid%2==0) && (nums[mid]==nums[mid+1]))) 
            key = check(nums, mid, r, (mid+r)/2);
        else key = check(nums, l, mid, (l+mid)/2);
        
        return key;
    }
    
    int singleNonDuplicate(vector<int>& nums) {
        if(nums.size()==1) return nums[0];
        else return check(nums, 0, nums.size()-1, nums.size()/2);
    }
};
