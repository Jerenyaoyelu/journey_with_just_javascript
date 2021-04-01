# Mental Model 心智模型
> [用于解释个体为现实世界中之某事所运作的内在认知历程](https://zh.wikipedia.org/wiki/%E5%BF%83%E6%99%BA%E6%A8%A1%E5%9E%8B)

<br/>

文章开头开门见山，抛出了一个问题：

以下代码执行后，a和b的值分别是什么？Dan要求我们在继续开始正文前，先在脑海中解决这个问题。

```javascript
let a = 10;
let b = a;
a = 0;
```


大家可能觉得，这不是很简单么。没错，是很简单，但算出a和b不是本文的目的，本文的目的在于通过这段代码来解释本文的主旨：`Mental Model`。

<br/>

## What’s a Mental Model? 什么是心智模型？

心智模型是当对面一块代码时，脑子里对其内部发生的事情形成的一种认知和帮助理解。他们可能是视觉、空间和机制的一种心理捷径。比方说前面代码中的`let a = 10`，你可能脑子里会想：哦，声明`a`，然后把10赋值给`a`。但到底什么是声明`a`？什么是赋值`a`？在你的脑子让你感觉自己理解了这两个过程的过程就是这个心智模型在起作用。这种直觉（感觉）将会伴随我们一生，影响着我们如何理解解读代码。

可能你会问，那即便知道了这个跟我们学习javascript又有什么关系呢？

大有关系！因为你的心智模型可能一开始就是错了，或者跑偏了，再或者你也从来没有求证过是否正确。而这些可能会导致你在开发过程中发生一些错误，或使自己编程能力瓶颈更低。准确有用的心智模型可以帮助你更快的定位修复、理解别人的代码以及对自己的代码也更加的自信。

这便是Dan大佬开始`Just Javascript`项目的初衷。

(提一嘴，正确答案是：`a = 0`，`b = 10`)

<br/>

## Coding, Fast and Slow 快且慢的编程

这里引用了人脑内的两种机制：fast and slow system. fast system擅长模式匹配和直觉反应，但不擅长计划。slow system则负责复杂的逻辑推理、从事活动或者数学证明等。因为slow system是很累人的，所以人的潜意识里都希望用fast system，即便是从事像编程之类的智慧任务。

Dan大佬随后用了一段代码解释了这个“定律” -- 果然我也毫不意外的没能逃出这个定律的魔掌。

快速的阅读和理解一下代码：

```javascript
function duplicateSpreadsheet(original) {
  if (original.hasPendingChanges) {
    throw new Error('You need to save the file before you can duplicate it.');
  }
  let copy = {
    created: Date.now(),
    author: original.author,
    cells: original.cells,
    metadata: original.metadata,
  };
  copy.metadata.title = 'Copy of ' + original.metadata.title;
  return copy;
}
```

你是不是得到以下结论？
- 这个方法是复制文件的。
- 如果文件没保存，这个方法会报错。
- 这个方法会给复制的文件命名为`Copy of`什么什么。

是的，没错，我也得出了这些结论。但是你有没有发现，这段代码其实隐藏着一个大bug！！

（想一下，是什么呢？回到前面在看下这段代码，看看你是用哪种system去解读，然后在继续往下看）

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

就是你在完成复制和命名的同时，不小心将源文件的名字也改了！！！

> 因为再给`copy.metadata`赋值的时候，是将`original.metadata`的引用赋值过去，这时候`copy`和`original`的`metadata`都引用自同一个数据源。所以改变`copy.metadata.title`，也就相当于改变了`original.metadata.title`

> 正确的写法应该是：
```javascript
// 用es6的解构语法
let copy = {
    created: Date.now(),
    author: original.author,
    cells: original.cells,
    metadata: {...original.metadata},
  };

// 或者assign
let copy = {
    created: Date.now(),
    author: original.author,
    cells: original.cells,
    metadata: Object.assign({},original.metadata),
  };
```

fast system专注在表面、注释和整体的结构，但slow system会一步一步的去追逐。模型内存执行代码的流程本来就很难了，而这种努力却浪费在错误的心智模型上。这就是为什么正确的心智模型是如此重要！
