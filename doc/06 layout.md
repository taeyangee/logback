参考：http://logback.qos.ch/manual/layouts.html

# logback-classic 中的 PatternLayout
- 都是针对ILoggerEvent做的处理链
- 关键实现 PatternLayout
    - The conversion pattern：PatternLayout主要将log event格式化，同时格式可配置，有点像c语言的printf
    - conversion specifiers 转换符号： 一个`%xxx`就是转换符
    - conversion specifiers converter：显然，就是转换符的处理器， pattern文件夹底下很多实现
    - 常见的conversion specifiers modifiers
        - Format modifiers
        - MDC modifiers : context信息带入
        - Coloring modifiers
        - Evaluator modifiers：作用就是动态判定一个modifier是否生效， 实现是基于JaninoEventEvaluator，
    - PatternLayoutEncoder vs PatternLayout: 因为设计Encoder，但是暂时又没什么用， 就简单wrap一下PatternLayout，叫做PatternLayoutEncoder

# logback-access 中的 PatternLayout
- logback-access layouts are mere adaptations of logback-classic layouts
