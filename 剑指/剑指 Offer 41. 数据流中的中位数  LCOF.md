```js
var MedianFinder = function() {
    this.arr = []
};

MedianFinder.prototype.addNum = function(num) {
    const n = this.arr.length
    // 找到第一个大于等于num的数
    if (n==0||this.arr[n-1]<num) this.arr.push(num)
    else {
        let l = 0, r = n-1
        while (l<r) {
            const m = (l+r)>>1
            if (this.arr[m]>=num) r = m
            else l = m+1
        }
        this.arr.splice(l,0,num)
    }
};

MedianFinder.prototype.findMedian = function() {
    const n = this.arr.length
    if ((n&1)===0) return (this.arr[n>>1]+this.arr[(n>>1)-1])/2
    else return this.arr[n>>1]
};
```

思路：与第295题相同。用数组实现的话每次插入时间复杂度O(n)，每次查找中位数时间复杂度O(1)。

```js
class MaxHeap {
    constructor(arr=[], k=Number.MAX_SAFE_INTEGER) {
        this.heap = []
        this.k = k
        for (const num of arr) this.push(num)
    }
    push(num) {
        this.heap.push(num)
        let idx = this.heap.length-1
        // 向上调整
        while (idx>0) {
            const idx_parent = (idx-1)>>1
            if (this.heap[idx_parent]>=this.heap[idx]) break
            [this.heap[idx_parent],this.heap[idx]] = [this.heap[idx],this.heap[idx_parent]]
            idx = idx_parent
        }
        // 向下调整
        while (idx < this.heap.length) {
            const inf = Number.MAX_VALUE
            const idx_left = idx * 2 + 1, left = idx_left < this.heap.length ? this.heap[idx_left] : -inf
            const idx_right = idx * 2 + 2, right = idx_right < this.heap.length ? this.heap[idx_right] : -inf
            if (left > right && left > this.heap[idx]) {
                [this.heap[idx_left], this.heap[idx]] = [this.heap[idx], this.heap[idx_left]]
                idx = idx_left
            } else if (right >= left && right > this.heap[idx]) {
                [this.heap[idx_right], this.heap[idx]] = [this.heap[idx], this.heap[idx_right]]
                idx = idx_right
            } else break
        }
    }
    pop() {
        if (this.heap.length==0) return
        if (this.heap.length==1) return this.heap.pop()
        const res = this.heap[0]
        this.heap[0] = this.heap.pop()
        // 向下调整
        let idx = 0
        while (idx < this.heap.length) {
            const inf = Number.MAX_VALUE
            const idx_left = idx * 2 + 1, left = idx_left < this.heap.length ? this.heap[idx_left] : -inf
            const idx_right = idx * 2 + 2, right = idx_right < this.heap.length ? this.heap[idx_right] : -inf
            if (left > right && left > this.heap[idx]) {
                [this.heap[idx_left], this.heap[idx]] = [this.heap[idx], this.heap[idx_left]]
                idx = idx_left
            } else if (right >= left && right > this.heap[idx]) {
                [this.heap[idx_right], this.heap[idx]] = [this.heap[idx], this.heap[idx_right]]
                idx = idx_right
            } else break
        }
        return res
    }
    size() {
        return this.heap.length
    }
    top() {
        return this.heap[0]||null
    }
}

class MinHeap {
    constructor(arr=[], k=Number.MAX_SAFE_INTEGER) {
        this.heap = []
        this.k = k
        for (const num of arr) this.push(num)
    }
    push(num) {
        this.heap.push(num)
        let idx = this.heap.length-1
        // 向上调整
        while (idx>0) {
            const idx_parent = (idx-1)>>1
            if (this.heap[idx_parent]<=this.heap[idx]) break
            [this.heap[idx_parent],this.heap[idx]] = [this.heap[idx],this.heap[idx_parent]]
            idx = idx_parent
        }
        // 向下调整
        while (idx < this.heap.length) {
            const inf = Number.MAX_VALUE
            const idx_left = idx * 2 + 1, left = idx_left < this.heap.length ? this.heap[idx_left] : inf
            const idx_right = idx * 2 + 2, right = idx_right < this.heap.length ? this.heap[idx_right] : inf
            if (left < right && left < this.heap[idx]) {
                [this.heap[idx_left], this.heap[idx]] = [this.heap[idx], this.heap[idx_left]]
                idx = idx_left
            } else if (right <= left && right < this.heap[idx]) {
                [this.heap[idx_right], this.heap[idx]] = [this.heap[idx], this.heap[idx_right]]
                idx = idx_right
            } else break
        }
    }
    pop() {
        if (this.heap.length==0) return
        if (this.heap.length==1) return this.heap.pop()
        const res = this.heap[0]
        this.heap[0] = this.heap.pop()
        // 向下调整
        let idx = 0
        while (idx < this.heap.length) {
            const inf = Number.MAX_VALUE
            const idx_left = idx * 2 + 1, left = idx_left < this.heap.length ? this.heap[idx_left] : inf
            const idx_right = idx * 2 + 2, right = idx_right < this.heap.length ? this.heap[idx_right] : inf
            if (left < right && left < this.heap[idx]) {
                [this.heap[idx_left], this.heap[idx]] = [this.heap[idx], this.heap[idx_left]]
                idx = idx_left
            } else if (right <= left && right < this.heap[idx]) {
                [this.heap[idx_right], this.heap[idx]] = [this.heap[idx], this.heap[idx_right]]
                idx = idx_right
            } else break
        }
        return res
    }
    size() {
        return this.heap.length
    }
    top() {
        return this.heap[0]||null
    }
}

var MedianFinder = function() {
    this.maxHeap = new MaxHeap()
    this.minHeap = new MinHeap()
};

MedianFinder.prototype.addNum = function(num) {
    if (this.maxHeap.size()==this.minHeap.size()) {
        this.maxHeap.push(num)
        this.minHeap.push(this.maxHeap.pop())
    } else {
        this.minHeap.push(num)
        this.maxHeap.push(this.minHeap.pop())
    }
};


MedianFinder.prototype.findMedian = function() {
    return this.minHeap.size()==this.maxHeap.size()?(this.minHeap.top()+this.maxHeap.top())/2:this.minHeap.top()
};
```

