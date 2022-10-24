


## 类型转换
+ 给你两个由数字组成的字符串"111"，“222”之类的，求它们相加的和，比如"333"，怎么做  
数字可能会很大，超过number安全范围
```js
let a = '1111'
let b = '222'
let max = Math.max(a.length, b.length)
let min = Math.min(a.length, b.length)
let carry = 0
let res = 0
  
b = '0'.repeat(max - min) + b

for (let i = 1; i <= max; i++) {
  let temp = Number(a[a.length - i]) + Number(b[b.length - i]) + carry;
  carry = temp > 9 ? 1 : 0
  temp %= 10
  res += Math.pow(10, i - 1) * temp
}
res += carry * Math.pow(10, max)
console.log(res)
```