# 2 源文件基础

## 2.1 文件名

文件名必须全部为小写，并且可以包括下划线(`_`)和和破折号(`-`)，但不包括其他标点符号。 遵循您的项目使用的约定。 文件名的扩展名必须是 `.js`。

## 2.2 文件编码: UTF-8

源文件使用 UFT-8 编码。

## 2.3 特殊字符

### 2.3.1 空白字符

除了行终止符序列，ASCII水平空格字符（0x20）是在源文件中任何位置出现的唯一的空格字符。 这意味着：

* 字符串文字中的所有其他空格字符都将被转义
* 制表符不用于缩进

### 2.3.2 特殊转义序列

对于具有特殊转义序列（\'，\“，\\，\b，\f，\n，\r，\t，\v）的任何字符，使用该序列而不是相应的数字转义 \x0a，\u000a或\u{a}）。从不使用旧的八进制转义。

### 2.3.3 非 ASC-II 字符

对于剩余的非 ASC-II 字符，是使用实际的 Unicode 字符 (例如 ∞) ，还是使用等价的十六进制或 Unicode 转义 (例如 \u221e)，取决于哪个能使代码更容易阅读和理解。

> Tip：在使用 Unicode 转义符或是一些实际的 Unicode 字符时，给出一些注释将会非常有助于理解。

例如：

```
const units = 'μs';`                						| 最佳，即使没有注释也非常清晰
const units = '\u03bcs'; // 'μs'`   						| 允许，但没有理由这样做
String unitAbbrev = "\u03bcs"; // Greek letter mu, "s"    	| 允许，但这样做显得笨拙还容易出错
String unitAbbrev = "\u03bcs";                            	| 很糟，读者根本看不出这是什么
return '\ufeff' + content; // byte order mark             	| 很好，对于非打印字符，使用转义，并在必要时写上注释
```

> Tip: 不要因为害怕某些程序可能无法正确处理非ASCII字符而降低代码的可读性。 如果发生这种情况，这些程序被打破，它们必须是固定的。
