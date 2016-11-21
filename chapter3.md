# 3 源文件结构

一个源文件包含(按顺序的):

1. 许可证或版权信息(如有需要)
2. `@fileoverview` JSDoc(如有需要)
3. `goog.module` 语句
4. `goog.require` 语句
5. 文件实现

各部分 **相互间隔一行**，只有文件实现可以间隔 1 或 2 行。

## 3.1 许可证或版权信息

如果一个文件包含许可证或版权信息，那么它应当被放在文件最前面。

## 3.2 `@fileoverview` JSDoc

有关格式化规则，请参阅7.5顶级/文件级注释。

## 3.3 `goog.module` 语句

`goog.module` 语句不换行，列限制([4.4节](# 4.4))并不适用于此语句。

单个 `goog.module` 语句后面可选调用 `goog.module.declareLegacyNamespace();` 和/或 `goog.setTestOnly();` 声明。尽量避免使用 `goog.module.declareLegacyNamespace()`。

### 3.3.1 `goog.module.declareLegacyNamespace`

可使用 `goog.module.declareLegacyNamespace` 简单地过渡到传统命名空间，但有一些命名限制。由于子模块名称必须在父命名空间之后创建，所以此名称不能是任何其他 `goog.module` 的子元素或父元素(例如， `goog.module('parent');` 和 `goog.module('parent.child');` 不能同时存在，同理 `goog.module('parent');` 和 `goog.module('parent.child.grandchild');` 也不能)

### 3.3.2 ES6 模块

不要使用 ES6 模块(即导入和导出关键字)，因为它们的语义还没有最终确定。一旦 ES6 语义被完整确立，将重新考虑本条规则。

## 3.4 `goog.require` 语句

通过 `goog.require` 完成导入，在模块声明之后即被分组。每个 `goog.require` 都会被分配给单个常量别名或者解构成几个常量别名。无论在代码中还是在类型注释中，在引用所需的依赖关系时这些别名是唯一可识标识。除了作为 `goog.require` 的参数，完全限定名称从不使用。 如果模块仅导入其副作用，则可以省略该分配，但是完全限定名称可能不会显示在文件中的任何其他位置。 别名名称应该尽可能匹配导入的模块名称的最后一个点分隔的组件，尽管可能包括额外的组件（如果有必要，别名的外壳仍能正确识别其类型），或者如果显着改进 可读性。 `goog.require` 语句可能不会显示在文件中的任何其他位置。



