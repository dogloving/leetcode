```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var maxValue = function(grid) {
    for (let i = 0; i < grid.length; i++) {
        for (let j = 0; j < grid[0].length; j++) {
            let up = i-1>=0?grid[i-1][j]:0, left = j-1>=0?grid[i][j-1]:0
            grid[i][j] += Math.max(up,left)
        }
    }
    return grid[grid.length-1][grid[0].length-1]
};
```

