# logger的阅读方向
- logger的base rule（effective level的继承、base rule的运行）
- Parameterized logging
```java
// 原始
logger.debug("Entry number: " + i + " is " + String.valueOf(entry[i]));
// Parameterized logging特性
logger.debug("The entry is {}.", entry);
```

# 关键流程 - Log.info()之后都发生了什么
see also http://logback.qos.ch/manual/architecture.html
1. Get the filter chain decision
2. Apply the basic selection rule
3. Create a LoggingEvent object
4. Invoking appenders
5. Formatting the output
6. Sending out the LoggingEvent