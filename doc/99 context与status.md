# context vs statusManager
[摘自configuration.html](http://logback.qos.ch/manual/configuration.html)
```text
Logback collects its internal status data in a StatusManager object, accessible via the LoggerContext.
```
```text
every logger is attached to a logger context
```
# statusManager
statusManager支持监听机制 ([摘自configuration.html](http://logback.qos.ch/manual/configuration.html))
```java
LoggerContext lc = (LoggerContext) LoggerFactory.getILoggerFactory(); 
StatusManager statusManager = lc.getStatusManager();
OnConsoleStatusListener onConsoleListener = new OnConsoleStatusListener();
statusManager.add(onConsoleListener);
```
