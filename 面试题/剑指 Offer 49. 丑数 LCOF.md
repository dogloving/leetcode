```js
/**
 * @param {number} n
 * @return {number}
 */
var nthUglyNumber = function(n) {
    let arr = [1]
    let idx2 = 0, idx3 = 0, idx5 = 0
    while (arr.length!=n) {
        let num2 = arr[idx2]*2, num3 = arr[idx3]*3, num5 = arr[idx5]*5
        if (num2<=num3&&num2<=num5) {
            if (num2!=arr[arr.length-1]) arr.push(num2)
            idx2++
        } else if (num3<=num2&&num3<=num5) {
            if (num3!=arr[arr.length-1]) arr.push(num3)
            idx3++
        } else if (num5<=num3&&num5<=num2) {
            if (num5!=arr[arr.length-1]) arr.push(num5)
            idx5++
        }
    }
    return arr[n-1]
};
```

