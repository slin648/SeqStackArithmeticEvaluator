# SeqStackArithmeticEvaluator
DS实验3 第一部分 顺序栈实现四则运算

程序实现了输入四则运算表达式，然后进行运算的功能。受限于本人水平，程序仅能支持 + - * / （ ）这几种运算符号，输入的数字必须为整数，且不能支持变量输入。 
程序使用了顺序栈的数据结构，具体使用了数组方式实现。 程序的主要流程为: 
首先从键盘读取字符串形式的算式，通过利用符号和数字的ASCII码的差异，将字符串形式的算式保存至整数型数组中，此时数组中为中缀表达式。
使用一个栈，将数组中的中缀表达式转化为后缀表达式并存储在另一个数组中，再使用另一个栈将后缀表达式进行计算，最后输出栈中的所剩元素，即为所求值。

将中缀表达式转化为后缀表达式的算法如下：

1.遍历中缀表达式 

2.如果当前中缀元素为操作数，则直接将此操作数“输出”到后缀表达式尾端 

3.如果当前中缀元素为'*'，'/'或'('，直接push入操作符栈 

4.如果当前中缀元素为')'，则依次pop出栈顶操作符，“输出”到后缀表达式尾端，直至pop得到的是一个'('才停止，并丢弃该'(' 

5.如果当前中缀元素为'+'或'-'，则依次pop出栈顶操作符、“输出”到后缀表达式尾端，直至栈底（栈空）或pop得到了一个'('，若pop得到一个'('，将'('重新push入栈。达到这两个条件之一后，将此操作符（'+'或'-'）入栈。 

6.如果当前中缀元素为'='，则依次pop出栈顶操作符、“输出”到后缀表达式尾端，直至栈底（栈空）。

计算后缀表达式的算法如下： 
将后缀表达式从左到右依次遍历，如果当前元素为数字则入（操作数）栈，如果为操作符，则pop出栈顶两个元素（第一次pop出的是右操作数，第二次pop出的是左操作数）进行运算，
然后将计算结果再次入栈，直至表达式结束，此时操作数栈内理应只剩一个元素即表达式结果。
