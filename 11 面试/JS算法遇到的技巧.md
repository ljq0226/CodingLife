
(map.get(sum) || 0)

a/b | 0

```javascript
var evalRPN = function (tokens) {
    const map = new Map([
        ["+", (a, b) => +a + +b],
        ["-", (a, b) => b - a],
        ["*", (a, b) => a * b],
        ["/", (a, b) => (b / a) | 0],
    ])
    const stack = []
    for (const c of tokens) {
        if (!map.get(c)) {
            stack.push(c)
            continue
        }
        stack.push(map.get(c)(stack.pop(), stack.pop()))
    }
    return stack.pop()
};
```