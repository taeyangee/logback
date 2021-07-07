# 参考
- https://www.chenliny.com/archives/382/

# 作用
- 实现[basic_selection](http://logback.qos.ch/manual/architecture.html#basic_selection)
- 位置：一个appender可以持有多个Filter

# In logback-classic
- 主要有两大类Filter, Regular Filter 和 TurboFilter

## RegularFilter
LevelFilter:
```xml
<filter class="ch.qos.logback.classic.filter.LevelFilter">
  <level>INFO</level>
  <onMatch>ACCEPT</onMatch>
  <onMismatch>DENY</onMismatch>
</filter>
```
ThresholdFilter
```xml
<filter class="ch.qos.logback.classic.filter.ThresholdFilter">
      <level>INFO</level>
    </filter>
```
EvaluatorFilter:基于表达式的filter

## TurboFilter
TurboFilter的租用
- TurboFilter vs RegularFilter:原理差不多。但是TurboFilter对象被绑定刚在logger上下文中
- 因此,作用范围有差别:在使用给定的appender以及每次发出的日志请求都会调用TurboFilter对象。
- TurboFilter可以为日志事件提供高性能的过滤，即使是在事件被创建之前。

MDC（Mapped Diagnostic Context）
- 全称：诊断上下文
- 场景：大部分的分布式系统需要同时处理多个客户端。在一个系统典型的多线程实现中，不同的线程处理不同的客户端。一种可能但是不建议的方式是在每个客户端实例化一个新的且独立的 log­ger，来区分一个客户端与另一个客户端的日志输出。这种方式会导致 log­ger 急剧增加并且会增加维护成本。
- 解决思路：一种轻量级的技术是给每个为客户端服务的 log­ger 打一个标记。Neil Har­ri­son 在 Patterns for Logging Diagnostic Messages in Pat­tern Lan­guages of Pro­gram De­sign 3, edited by R. Mar­tin, D. Riehle, and F. Buschmann (Ad­di­son-Wes­ley, 1997) 这本书中描述了这种方法。log­back 在 SLF4J API 利用了这种技术的变体：诊断上下文映射 (MDC)。log­back 在 SLF4J API 利用了这种技术的变体：诊断上下文映射 (MDC)。