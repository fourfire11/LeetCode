# Flood Fill

###### tags: `LeetCode`

## 題目

An `image` is represented by a 2-D array of integers, each integer representing the pixel value of the image (from 0 to 65535).

Given a coordinate `(sr, sc)` representing the starting pixel (row and column) of the flood fill, and a pixel value `newColor`, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image.

**Example 1:**

    Input: 
    image = [[1,1,1],[1,1,0],[1,0,1]]
    sr = 1, sc = 1, newColor = 2
    Output: [[2,2,2],[2,2,0],[2,0,1]]
    Explanation: 
    From the center of the image (with position (sr, sc) = (1, 1)), all pixels connected by a path of the same color as the starting pixel are colored with the new color.
    Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3326/)


## C++程式碼 (by DFS)
```C++
class Solution {
public:
    void DFS(vector<vector<int>>& image, int curR, int curC, int oriColor, int newColor){
        // image[curR][curC]與oriColor不相同有兩種情況
        // 1. image[curR][curC]已經被更改成newColor
        // 2. image[curR][curC]本來的顏色就與image[curR][curC]不同，不需更改
        // 不管是哪種情況，皆不需要再做更動，故return
        if(image[curR][curC] != oriColor) return; 
        image[curR][curC] = newColor;
        // 往上走
        if(curR > 0) DFS(image, curR-1, curC, oriColor, newColor);
        // 往下走
        if(curR+1 < image.size()) DFS(image, curR+1, curC, oriColor, newColor);
        // 往右走
        if(curC+1 < image[0].size()) DFS(image, curR, curC+1, oriColor, newColor);
        // 往左走
        if(curC > 0) DFS(image, curR, curC-1, oriColor, newColor);
    }
    
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor) {
        // 若image[sr][sc]的顏色與newColor顏色相同，則不需要更改
        if(image[sr][sc] != newColor) DFS(image, sr, sc, image[sr][sc], newColor);
        return image;
    }
};
