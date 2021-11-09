# 异步流Blog

## [初识 Kotlin Flow](https://blog.yujinyan.me/posts/kotlin-flow-introduction/)

### Flow：可以 suspend 的 Sequence

实际上和 Sequence 一样，Flow 的终端操作符才是驱动整个数据流的“原动力”。如果没有终端操作符，只引用了若干 map、filter 中间操作符，相当于只搭建了一个数据管道，Flow builder 中的代码不会运行，数据不会流动。 这种 Flow 被称作「冷流」

### Flow 的额外保证

#### 上下文保存（Context preservation）

所以，**Kotlin 协程库的 Flow 实现会检查 emit 和 collect 在同一个协程里执行**，否则会直接抛出异常

注意，**Flow 禁止的是在不同的协程 emit 数据**，并不是说 Flow 块中不能切换 Context

## Lib

https://github.com/ReactiveCircus/FlowBinding

