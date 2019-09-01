## -  Number of Islands

### 代码
```
int numIslands(vector<vector<char>>& grid) 
{
    int count = 0;

    for(int i = 0; i < grid.size(); i++)    //遍历所有小岛
    {
        for(int j = 0; j < grid[i].size(); j++)
        {                
            if (grid[i][j] == '1')    //如果是1
            {                    
                count ++;    //增加小岛计数
                helper(grid, i, j);    //炸掉邻接小岛
            }
        }
    }
    return count;        
}

void helper(vector<vector<char>>& grid, int i, int j)
{
    //i,j不在区域范围内，或者i,j位置本身是海洋
    if (i < 0 || i >= grid.size() || j < 0 || j >= grid[i].size() || grid[i][j] == '0')
        return;    //直接返回
    grid[i][j] = '0';    //炸掉当前小岛
    helper(grid, i - 1, j);    //递归探测上边情况
    helper(grid, i + 1, j);    //递归探测下边情况
    helper(grid, i, j + 1);    //递归探测右边情况
    helper(grid, i, j - 1);    //递归探测左边情况
}
