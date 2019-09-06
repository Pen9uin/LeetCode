## - Spiral Matrix

### 描述
```
Given a matrix of m x n elements (m rows, ncolumns), return all elements of the matrix in spiral order.

Example:
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output: [1,2,3,6,9,8,7,4,5]
```

### 代码
```
class Solution {
public:
    vector<int> printMatrix(vector<vector<int> > matrix) {
        int rows = matrix.size(); 
        int cols = matrix[0].size();
        vector<int> result;
        
        if(rows == 0 && cols == 0)
            return result;
            
        int left = 0, right = cols - 1, top = 0, bottom = rows - 1;
        
        while(left <= right && top <= bottom){
            for(int i = left; i <= right; ++i)
                result.push_back(matrix[top][i]);
            
            for(int i = top + 1; i <= bottom; ++i)
                result.push_back(matrix[i][right]);
            
            if(top != bottom){
                for(int i = right - 1; i >= left; --i){
                    result.push_back(matrix[bottom][i]);
                }
            }
            if(left != right){
                for(int i = bottom - 1; i > top; --i){
                    result.push_back(matrix[i][left]);
                }
            }
            left++, top++, right--, bottom--;
        }
        return result;
    }
};
```
