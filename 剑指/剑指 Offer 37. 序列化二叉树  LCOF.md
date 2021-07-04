```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */

/**
 * Encodes a tree to a single string.
 *
 * @param {TreeNode} root
 * @return {string}
 */
var serialize = function(root) {
    if (!root) return ''
    let res = root.val.toString()+','
    let q = [root]
    while (q.length) {
        let node = q[0]
        q.shift()
        if (node.left) {
            q.push(node.left)
            res = res + node.left.val.toString() + ','
        } else res = res + 'null,'
        if (node.right) {
            q.push(node.right)
            res = res + node.right.val.toString() + ','
        } else res = res + 'null,'
    }
    return res
};

/**
 * Decodes your encoded data to tree.
 *
 * @param {string} data
 * @return {TreeNode}
 */
var deserialize = function(data) {
    if (data.length==0) return null
    data = data.split(',')
    let idx = 0
    let nodes = []
    for (let i = 0; i < data.length;i++) {
        if (nodes.length==0) {
            let d = data[i]
            nodes.push(new TreeNode(parseInt(d)))
        } else {
            let d1 = data[i]
            i++
            let d2 = data[i]
            if (d1!='null') {
                let node = new TreeNode(parseInt(d1))
                nodes.push(node)
                nodes[idx].left = node
            }
            if (d2!='null') {
                let node = new TreeNode(parseInt(d2))
                nodes.push(node)
                nodes[idx].right = node
            }
            idx++
        }
    }
    return nodes[0]
};

/**
 * Your functions will be called as such:
 * deserialize(serialize(root));
 */
```

```tsx
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */

/**
 * Encodes a tree to a single string.
 *
 * @param {TreeNode} root
 * @return {string}
 */
var serialize = function(root) {
    if (root === null) return '';
    let res = root.val.toString();
    const q = [root];
    while (q.length) {
        const node = q.shift();
        if (node.left) {
            res += `,${node.left.val}`;
            q.push(node.left);
        } else res += ',null';
        if (node.right) {
            res += `,${node.right.val}`;
            q.push(node.right);
        } else res += ',null';
    }
    return res;
};

/**
 * Decodes your encoded data to tree.
 *
 * @param {string} data
 * @return {TreeNode}
 */
var deserialize = function(data) {
    if (data === '') return null;
    const sNode = data.split(',');
    const res = [new TreeNode(parseInt(sNode[0]))];
    let idx = 0;
    for (let i = 1; i < sNode.length; i+=2,idx++) {
        const left = sNode[i], right = sNode[i+1];
        if (left !== 'null' && left !== '') {
            const leftChildNode = new TreeNode(parseInt(left));
            res[idx].left = leftChildNode;
            res.push(leftChildNode);
        }
        if (right !== 'null' && right !== '') {
            const rightChildNode = new TreeNode(parseInt(right));
            res[idx].right = rightChildNode;
            res.push(rightChildNode);
        }
    }
    return res[0];
};

/**
 * Your functions will be called as such:
 * deserialize(serialize(root));
 */
```