# HttpRequestCallBack

位置在com.xh.framework.net.HttpRequestCallBack

HttpRequestCallBack是网络数据解析回调接口

```java
/**
  * error_code为0时回调
  * @param result
  */
  void onSuccess(T result);
/**
 * 异常回调
 * @param msg
 */
void onException(String msg);

/**
  * error_code为非0时回调,可以根据不同的code进行逻辑处理
  * @param code
  * @param msg
  */
void onError(int code,String msg);
```



