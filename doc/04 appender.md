# 概要
[Appender类图](./Appender.uml)
参考：http://logback.qos.ch/manual/appenders.html

# Appender 接口

# AppenderBase 框架类
- 实现了base rule的几个步骤
- This implementation of the doAppend() method is synchronized. 
- guard属性用于阻止append方法的循环调用
- start属性：判断Appender是否启用，启用前不能工作。
    - 失败的请求会被记录到Appender的StatusManager
    - StatusManager还有防止消息泛红的机制
- FilterChainDecision

# Appender的几种实现类
- ConsoleAppender
- FileAppender
- RollingFileAppender 及其策略 TimeBasedRollingPolicy、Size and time based rolling policy、FixedWindowRollingPolicy
