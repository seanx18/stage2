
### 第三阶段，再次进行一人中文，一人英文的翻译练习。

- 这3个阶段可反复进行。

中文：早上好，我非常紧张，因为我三十分钟后有一个编程技能测试面试，所以我得去换衣服准备一下。

英文：Good morning, I'm very nervous because I have <font color="#ff0000">a coding skills test interview</font> in 30 minutes, so I have to go get changed and get ready.

中文：老实说，我不知道自己要怎么做，因为有时候我觉得这些逻辑很难。

英文：I honestly don't know how I'm going to do, <font color="#ff0000">because these logics are quite difficult for me to understand.</font>

中文：但我会回来告诉你们他们问了我什么，因为我知道这对我有帮助。

英文：But I'm going to come back here and let you know what they ask me, <font color="#ff0000">because I know I would find that helpful</font>.

中文：这是一个前端网页开发职位的面试，所以我会告诉你们他们让我解决了哪些技术问题。 英文：This is for a front-end web developer position, so I'll let you know <font color="#ff0000">what technical questions they ask me to figure out / resolve</font>.

中文：现在我做完了。哦天哪，好的，我完成了。

英文：Now I did. Oh my god, okay, I finished.

中文：老实说，没那么糟糕。我真的很紧张，就像我忘了我的GitHub命令。

英文：It was not that bad, honestly. I was really nervous, I was like, I forget my GitHub commands.

中文：这有点难，因为他让我创建一个新文件夹，然后给它指定一个Git仓库，并更改分支，比如创建一个主分支，然后切换到另一个叫Feature的分支。

英文：That was kind of hard, because he asked me to make a new folder and <font color="#ff0000">assign a Git repo to it</font>, and then change branches, like create a master branch, <font color="#ff0000">and then check out to another branch called Feature</font>.

---

### Q&A
**Q1: What are the types and values of null and undefined?  **

A: Both null and undefined are primitive data types in JavaScript, with their respective values being exactly 'null' for null and 'undefined' for undefined.

**Q2: What do undefined and null represent?  **

A: Undefined represents an undefined value, often seen when variables are declared but not defined. Null represents an empty object and is used for initializing variables that may eventually hold an object.

**Q3: Can undefined be used as a variable name?  **

A: Yes, undefined is not a reserved word in JavaScript, allowing its use as a variable name. However, this practice is risky and can affect how undefined values are determined. A secure way to obtain an undefined value is using 'void 0'.

**Q4: How do typeof operations on null and undefined differ?  **

A: When using typeof on null, it returns "object", a behavior considered a legacy bug. For undefined, typeof returns "undefined".

**Q5: How do null and undefined compare with double and triple equals?  **

A: When compared with double equals `==`, null and undefined are considered equal, returning true. However, when compared with triple equals `===`, they are not considered equal, returning false, highlighting their distinctiveness despite similarities.

---
### null和undefined区别

The difference between null and undefined

首先 Undefined 和 Null 都是基本数据类型，这两个基本数据类型分别都只有一个值，就是 undefined 和 null。

First of all, Undefined and Null are both basic data types. Each of these two basic data types has only one value, which is undefined and null.

undefined 代表的含义是**未定义**，null 代表的含义是**空对象**。一般变量声明了但还没有定义的时候会返回 undefined，null主要用于赋值给一些可能会返回对象的变量，作为初始化。

Undefined means undefined, while null means empty object. When a general variable is declared but not yet defined, it will return undefined. null is mainly used to assign values to variables that may return objects as initialization.

undefined 在 JavaScript 中不是一个保留字，这意味着可以使用 undefined 来作为一个变量名，但是这样的做法是非常危险的，它会影响对 undefined 值的判断。我们可以通过一些方法获得安全的 undefined 值，比如说 void 0。

Undefined is not a reserved word in JavaScript, which means that it can be used as a variable name, but this approach is very dangerous as it can affect the judgment of the undefined value. We can obtain secure undefined values through some methods, such as void 0.

当对这两种类型使用 typeof 进行判断时，Null 类型化会返回 “object”，这是一个历史遗留的问题。当使用双等号对两种类型的值进行比较时会返回 true，使用三个等号时会返回 false。

When using typeof to judge these two types, Null typing will return "object", which is a historical problem. Returns true when using a double equal sign to compare two types of values, and returns false when using a triple equal sign.

