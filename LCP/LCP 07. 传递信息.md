```javascript
/**
 * @param {number} n
 * @param {number[][]} relation
 * @param {number} k
 * @return {number}
 */
var numWays = function(n, relation, k) {
    let from_to = {}
    for (let r of relation) {
        if (r[0] in from_to) from_to[r[0]].add(r[1])
        else from_to[r[0]] = new Set([r[1]])
    }
    let q = [[0,0]]
    let res = 0
    while (q.length) {
        let node = q[0]
        q.shift()
        if (node[1]==k) {
            if (node[0]==n-1) res++
        } else {
            if (node[0] in from_to) {
                console.log('t')
                for (let to of from_to[node[0]]) q.push([to,node[1]+1])
            }
        }
    }
    return res
};
```

思路：上面是使用bfs，时间复杂度O(n!)级别。

下面介绍动态规划算法，时间复杂度O(nk)。令dp[i]\[j]表示传递了i轮到达玩家j手里的方法种数。dp[i]\[j]=sum(dp[i-1]\[s])，其中有relation[x]=[s,j]。由于每一轮只用到了上一轮的信息，所以我们无需使用二维数组进行存储，只用一维数组就能实现。

```tsx
function numWays(n: number, relation: number[][], k: number): number {
    let lastRound = new Array(n).fill(0);
    lastRound[0] = 1;
    while (k--) {
        const currentRound = new Array(n).fill(0);
        for (const [src, dst] of relation) {
            currentRound[dst] += lastRound[src];
        }
        lastRound = currentRound;
    }
    return lastRound[n-1];
};
```

