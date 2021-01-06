```javascript
/**
 * initialize your data structure here.
 */
var MinStack = function() {
    this.stack = []
    this.current_min = []
};

/** 
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function(x) {
    if (this.stack.length==0) {
        this.stack.push(x)
        this.current_min.push(x)
    } else {
        this.stack.push(x)
        this.current_min.push(Math.min(x,this.current_min[this.current_min.length-1]))
    }
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function() {
    this.stack.pop()
    this.current_min.pop()
};

/**
 * @return {number}
 */
MinStack.prototype.top = function() {
    return this.stack[this.stack.length-1]
};

/**
 * @return {number}
 */
MinStack.prototype.min = function() {
    return this.current_min[this.current_min.length-1]
};

/**
 * Your MinStack object will be instantiated and called as such:
 * var obj = new MinStack()
 * obj.push(x)
 * obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.min()
 */
```

