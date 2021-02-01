```js
/**
 * @param {number[]} arr
 * @param {number} k
 * @return {number[]}
 */
var getLeastNumbers = function(arr, k) {
    if (k==0) return []
    let heap = [arr[0]]
    // 建堆
    for (let i = 1; i < k; i++) {
        heap[i] = arr[i]
        // 向上调整
        let current = i
        while (current!=0) {
            let parent = Math.floor((current-1)/2)
            if (heap[current]<=heap[parent]) break
            [heap[current],heap[parent]] = [heap[parent],heap[current]]
            current = parent
        }
        // 向下调整
        while (current<=i) {
            let left = current*2+1, right = current*2+2
            let left_val = -1, right_val = -1
            if (left<=i) left_val = heap[left]
            if (right<=i) right_val = heap[right]
            if (left_val<right_val) {
                if (right_val>heap[current]) {
                    [heap[current],heap[right]] = [heap[right],heap[current]]
                    current = right
                } else break
            } else {
                if (left_val>heap[current]) {
                    [heap[current],heap[left]] = [heap[left],heap[current]]
                    current = left
                } else break
            }
        }
    }
    // 维护堆
    for (let i = k; i < arr.length; i++) {
        if (arr[i]>=heap[0]) continue
        heap[0] = arr[i]
        // 向下调整
        let current = 0
        while (current<k) {
            let left = current*2+1, right = current*2+2
            let left_val = -1, right_val = -1
            if (left<k) left_val = heap[left]
            if (right<k) right_val = heap[right]
            if (left_val<right_val) {
                if (right_val>heap[current]) {
                    [heap[current],heap[right]] = [heap[right],heap[current]]
                    current = right
                } else break
            } else {
                if (left_val>heap[current]) {
                    [heap[current],heap[left]] = [heap[left],heap[current]]
                    current = left
                } else break
            }
        }
    }
    return heap
};
```

思路：首先想到大根堆。