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

