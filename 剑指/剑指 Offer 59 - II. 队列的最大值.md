```javascript
var MaxQueue = function() {
    this.queue = []
    this.queue_max = []
};

/**
 * @return {number}
 */
MaxQueue.prototype.max_value = function() {
    return this.queue_max.length?this.queue_max[0]:-1
};

/** 
 * @param {number} value
 * @return {void}
 */
MaxQueue.prototype.push_back = function(value) {
    this.queue.push(value)
    while (this.queue_max.length&&this.queue_max[this.queue_max.length-1]<value) this.queue_max.pop()
    this.queue_max.push(value)
};

/**
 * @return {number}
 */
MaxQueue.prototype.pop_front = function() {
    if (this.queue.length==0) return -1
    let res = this.queue[0]
    this.queue.shift()
    if (res==this.queue_max[0]) this.queue_max.shift()
    return res
};

/**
 * Your MaxQueue object will be instantiated and called as such:
 * var obj = new MaxQueue()
 * var param_1 = obj.max_value()
 * obj.push_back(value)
 * var param_3 = obj.pop_front()
 */
```

