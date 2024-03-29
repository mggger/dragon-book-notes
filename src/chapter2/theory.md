# 一个简单的语法制导翻译器

一些概念:

**文法:** 用于描述程序设计语言语法的表示方法, 或称为上下文无关文法。 文法用于组织编译器前端.

比如java中的IF-else语句, 通常具有以下形式

```
if (expr) statment else statment 

可以用变量expr表示表达式， 变量stmt表示语句

stmt -> if (expr) stmt else stmt
```

像关键字```if``` 这样的词法元素称为 ```终结符号```。 像 ```expr``` 和```stmt```这样的变量表示终结符号的序列， 可以称为```非终结符号```.

**文法由下面4个元素组成:**

- 一个终结符号集合， 有时候被称为"词法单元"
- 一个非终结符号的集合， 它们有时被称为"语法变量"
- 一个产生式集合
- 指定一个非终结符号为开始符号

*** 

推导:  根据文法推到符号串时候， 首先从开始符号出发， 不断将某个非终结符号替换为该非终结符号的某个产生式的体。 可以从开始符号推到得到的所有终结符号串的集合为该文法定义的语言。

## 树的遍历

**深度遍历:** 尽可能地访问一个结点的尚未被访问的子结点. 
```
procedure visit(node N) {
    for (从左到右遍历N的每个子结点C) {
        visit(C);
    }

    xxx
}
```
**前序遍历:** 遍历一棵树， 如果动作在第一次访问一个结点时被执行
**后序遍历:** 遍历一棵树， 如果动作在最后离开节点前执行.


## 递归下降语法

递归下降分析方法是一种自顶向下的语法分析方法, 它使用一组递归过程来处理输入。

递归下降语法分析器有可能进入无限循环， 当出现一些产生式时， 分析器会出现无限循环. 比如```expr -> expr + term ```

左递归: 产生式 ```A -> Aa ``` 的右部最左符号是A自身， 非终结符号A和它的产生式称为左递归的.

右递归: 产生式 ```R -> aR ``` 的右部最右符合是R本身， 非终结符号R和它的产生式称为右递归的.

## 尾递归

如果一个过程体执行的最后一条语句是对该过程的递归调用， 那么这个调用就是称为是尾递归的.

## 三地址码
一旦抽象语法树构造完成， 我们就可以计算树中各结点的属性值并执行各节点中的代码片段， 进行进一步的分析和综合。 

