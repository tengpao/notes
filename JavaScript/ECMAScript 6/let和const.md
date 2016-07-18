## let和const

### let
- let声明的变量只在所在区块有效
- 不存在变量提升（必须先声明后使用）
- 声明的全局变量不再是全局对象的属性
- 暂时性死区
- 不允许重复声明

### const
- const声明时必须赋值
- const声明的复杂类型只指向变量的地址（保证变量的地址不变，并不保证该地址的数据不变）

> 块级作用域下面声明的函数会被提升到区块头部


## 变量解构赋值

```
var [a, b, c] = [1, 2, 3];

let [foo, [[bar], baz]] = [1, [[2], 3]];
foo // 1
bar // 2
baz // 3

var { foo, bar } = { foo: "aaa", bar: "bbb" };

let { log, sin, cos } = Math;
```

> [变量解构赋值用途](http://es6.ruanyifeng.com/#docs/destructuring#用途)