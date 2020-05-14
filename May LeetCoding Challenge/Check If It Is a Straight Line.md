# Check If It Is a Straight Line

###### tags: `LeetCode`

## 題目

You are given an array `coordinates`, `coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/10/15/untitled-diagram-2.jpg)

    Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
    Output: true

**Example 2:**

![](https://assets.leetcode.com/uploads/2019/10/09/untitled-diagram-1.jpg)

    Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
    Output: false

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3323/)


## C++程式碼(by 斜率是否相等)
```C++
class Solution {
public:
    bool checkStraightLine(vector<vector<int>>& coordinates) {
        if(coordinates.size()==2) return true;
        
        int x_0 = coordinates[0][0];
        int y_0 = coordinates[0][1];
        int dif_x = x_0 - coordinates[1][0];
        int dif_y = y_0 - coordinates[1][1];
        
        for(int i=2; i < coordinates.size(); i++){
            int x_i = coordinates[i][0];
            int y_i = coordinates[i][1];
            if((y_i-y_0)*dif_x != dif_y*(x_i-x_0)) return false;
        }
        return true;
    }
};
```

## C++程式碼(by cross product)
```C++
class Solution {
public:
    // cross=0 meaning the two vectors are parallel
    int cross(int oX, int oY, int aX, int aY, int bX, int bY){
        return (aX-oX) * (bY-oY) - (aY-oY) * (bX-oX);
    }
    
    bool checkStraightLine(vector<vector<int>>& coordinates) {
        if(coordinates.size()==2) return true;
        else{
            for(int i=1; i<coordinates.size(); i++){
                if(cross(coordinates[0][0], coordinates[0][1], coordinates[i-1][0], coordinates[i-1][1],
                coordinates[i][0], coordinates[i][1])!=0)
                    return false;                
            }
            return true;
        }
    }
};
```
