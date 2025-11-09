`as const`  是TS 中的一种类型断言，意思是当作常量处理，不要自动放宽类型。

什么是放宽类型限制：TS  在推断类型的时候会默认你可能想修改这个类型的值，所以会给一个更宽松、更通用的类型。

`as const` 主要做两件事：
1. 锁定值：把类型变成精确的字面量类型（不是宽泛的string/number）
2. 锁定结构：给所有属性加上`readonly` （不能修改）

```ts
const config ={
	host:'localhost',
	port: 3000
} //没有 as const 可修改的 类型：{ host: string, port: number }

const config = {
	host: 'localhost',
	prot: 3000
} as const  //不可修改的 类型：{ readonly host: "localhost", readonly port: 3000 }
```