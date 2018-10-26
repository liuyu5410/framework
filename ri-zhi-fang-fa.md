# 日志方法

---

为保证日志安全与优化显示，对日志功能进行了二次封装。

在项目中统一使用 XhLog 进行日志打印。

* ##### 实现在debug模式下进行打印，非debug模式下不打印日志。
* ##### 实现打印时同步输出日志文件、行数等信息。

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

#### 参考

com.xh.framework.log.XhLog

