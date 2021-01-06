```javascript
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var findNumberIn2DArray = function(matrix, target) {
    let m = matrix.length
    if (m==0) return false
    let n = matrix[0].length
    return search(matrix,target,0,0,m-1,n-1)
};
function search(matrix,target,x1,y1,x2,y2) {
    let m = matrix.length, n = matrix[0].length
    if (x1>=m||x2>=m||y1>=n||y2>=n||x1<0||x2<0||y1<0||y2<0||x1>x2||y1>y2) return false
    if (x1==x2&&y1==y2) return matrix[x1][y1]==target
    let x = Math.floor((x1+x2)/2), y = Math.floor((y1+y2)/2)
    if (matrix[x][y]==target) return true
    else if (matrix[x][y]<target) {
        return search(matrix,target,x1,y+1,x2,y2)||search(matrix,target,x1+1,y1,x2,y)
    } else {
        return search(matrix,target,x1,y1,x2,y-1)||search(matrix,target,x1,y,x-1,y2)
    }
}
```

