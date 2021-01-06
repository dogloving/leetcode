```javascript
/**
 * @param {string} command
 * @param {number[][]} obstacles
 * @param {number} x
 * @param {number} y
 * @return {boolean}
 */
var robot = function(command, obstacles, x, y) {
    let up = 0, right = 0
    for (let c of command) c=='U'?up++:right++
    let p = [0,0]
    let reachable = false
    // console.log(up,right)
    for (let c of command) {
        // 检查从p点经过整数次循环是否会碰到障碍物，即p点和障碍物之间横纵向距离是否为up和right整数倍，注意障碍物在目标点下面或左边都碰不到
        for (let o of obstacles) {
            if (o[0]>x||o[1]>y) continue
            let meet = check(o[0],o[1],p[0],p[1],up,right)
            if (meet) {
                console.log(p,o)
                return false
            }
        }
        // 检查能否从p点经过完整次循环到[x,y]
        if (!reachable) reachable = check(x,y,p[0],p[1],up,right)
        c=='U'?p[1]++:p[0]++
    }
    return reachable
};

function check(x,y,px,py,up,right) {
    let gap_right = x-px, gap_up = y-py
    if (gap_up<0||gap_right<0) return false
    if (gap_up==0&&gap_right==0) return true
    else if (gap_up==0||gap_right==0) return false
    return (gap_up%up==0&&gap_right%right==0&&gap_up/up==gap_right/right)
}

```

思路：