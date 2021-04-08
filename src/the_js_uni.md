# The JavaScript Universe
> JS宇宙，大概就是类似漫威宇宙、DC宇宙、唐探宇宙之类的吧 ：）

<br/>

同样的，本单元也是以一个问题开始：
```text
What is a value? 什么是value？
```

在JS宇宙中，value就是一样东西。但JS宇宙中也存在一些不是value的东西，比方说if语句，变量声明等。

<br/>

## Code and Values

- primitive values 原始值
> 具体可以看`Types of Values`

对于这类值，你无法在代码中改变或者影响他们。

- Objects and Functions 对象和方法
> 原始值之外的值

这类值是可以在代码中修改。

<br/>

## Expressions 表达式

你可以理解为是描述值的一段代码。

- Checking a Type 检查类型
```text
这里就讲了用typeof去做类型检查；一般不要括号，但有时候为了避免误会，需要使用括号，如一下代码：

console.log({});
...
```

<br/>

## Types of Values 值的类型

### Primitive Values 原始值

```javascript
Undefined // 用作未定义过的值
Null // 用作故意设为无的值
Booleans // 用作逻辑判断
Numbers // 用作数学计算
Strings // 用作文字
Symbols // 用作隐藏实现细节（不常用）
BigInts // 用作数学上的大整型（不常用）
```

> 注：
> - `typeof null`会返回`object`，而不会返回`null`，这其实是一个js的bug，但现在修复已经太迟了。关于这相关的历史，可以[看这里](https://2ality.com/2013/10/typeof-null.html).
> - `typeof typeof value`总是会放回`string`.

### Objects and Functions 对象和防范

```javascript
Objects // 用作组合相关数据和代码
Functions // 用作指向代码
```

虽然在JS中，可以说一切皆对象，但是`"hi".toUpperCase()`之类的像是一个对象但其实更多只是一种错觉。当我们这么用的时候，JS会创建一个wrapper对象包裹它，但很快就销毁了。