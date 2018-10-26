# 日志

为保证日志安全与优化显示，对日志功能进行了二次封装。

在项目中统一使用 XhLog 进行日志打印。

```java
XhLog.d(str);
XhLog.e(str);
XhLog.v(str);
XhLog.i(str);
XhLog.w(str);
XhLog.t(str);
XhLog.json(json);
XhLog.xml(xmlStr);
```



