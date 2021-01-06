```javascript
/**
 * @param {number[]} cont
 * @return {number[]}
 */
var fraction = function(cont) {
    let res = [cont[cont.length-1],1]
    for (let i = cont.length-2; i >= 0; i--) {
        res = [cont[i]*res[0]+res[1],res[0]]
    }
    // gcd
    let g = gcd(...res)
    return [res[0]/g,res[1]/g]
};
function gcd(a,b) {
    while (b) [a,b] = [b,a%b]
    return a
}
```

