# Values and Variables
老规矩，先上代码片段：
```javascript
let reaction = 'yikes';
reaction[0] = 'l';
console.log(reaction);
```

想一下，控制台会打印出什么？

在公布答案之前，先尝试重现（记录）下你思考的过程，一步步。如果有任何跳跃或者不确定在你当前的心智模型中，可以将他们写下来。有任何疑问就尽力去搞清楚，在继续往下看。

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

如果你觉得上面的代码会在控制台中打印`likes`，那么不好意思，你错的好离谱。答案是要么打印`yikes`，要么报错如果是在严格模式下。永远都不会打印`likes`。

<br/>

## Primitive Values Are Immutable 原始值是不可修改的
这类问题实际工作中可能比较少遇到，更多的可能是在面试中会出现。**原始值是无法修改的！**

上面的代码问题答错朋友你可能会疑问，字符串不是和数组差不多么，这么些数组都是ok的，为什么字符串不行？就是因为`string`是原始类型的值。

**所有原始类型的值都不可修改！**

所以自然也就不能设置`property`。

<br/>

## A Contradiction? 有矛盾？

现在来看看下面的例子：
```javascript
let pet = 'Narwhal';
pet = 'The Kraken';
console.log(pet);
```

想下这段代码会打印出什么？

没错就是`'The Kraken'`；这个时候你是不是一脸疑惑？？这不是和上面自相矛盾了吗？（如果没有，那就直接跳过下一部分内容）

<br/>

## Variables Are Wires

其实并不是，这部分代码是改变了`pet`这个变量指向的内存内容，并不是去改变原来的`'Narwhal'`。在JS宇宙里，变量和值是不一样的 --- 变量指向值。原始值不可变，但是变量可以改变指向！Dan大佬是这么理解这两者的关系的：
```text
In my universe, a variable is a wire. It has two ends and a direction: it starts from a name in my code and it ends pointing at some value in my universe.
```

简单的说就是，变量是一条有向线，连接着我代码中的变量名称和内存中的值，并指向这个值。

对变量我们可以做如下操作：
### Assigning a Value to a Variable 赋值

记住两条就行：
- 等式左边必须是`线` -- 变量
- 等式右边必须是表达式

### Reading a Value of a Variable 读值

```javascript
console.log(pet)
```
比方说log一个变量。但需要注意的是我们传给log的并不是这个变量（我们并不能把变量传给函数），而是把这个变量当前的值传给log函数。

你可能会问把变量当前的值传给函数，这怎么理解？其实`pet`也是一个表达式，当我们使用变量`pet`的时候，就相当于问JS它当前的值是什么，JS就会顺着`线`找到内存中的值并返回。

### Nouns and Verbs

在JS中无法传变量给函数，我们可以看一下下面这个例子：

```javascript
function double(x) {
  x = x * 2;
}

let money = 10;
double(money);
console.log(money); // ?
```

如果我们传进函数的是变量，那么log出来的自然应该是20。但并不是！log出来的依然是10. 我们只是将money的值传进去。

### Putting It Together

- 原始类型的值不可变
- 变量不是值
- 变量总是指向值
- 变量像一根线
