```javascript
/**
 * @param {string} s
 * @return {character}
 */
var firstUniqChar = function(s) {
    for (let i = 0; i < s.length; i++) {
        if (s.lastIndexOf(s[i])==i&&s.indexOf(s[i])==i) return s[i]
    }
    return ' '
};
```

