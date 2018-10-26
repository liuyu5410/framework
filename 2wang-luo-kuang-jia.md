# 网络框架

---

对应的类是com.xh.framework.net.HttpRequest.java

POST请求

```java
/**
 * post请求，不带加载框
 * @param activity activity
 * @param url url
 * @param httpParams 参数
 * @param callBack 回调接口
 * @param <T> 泛型,如果接口返回的是对象，直接传Bean，如果接口返回的是list,传List<Bean>
 */
 public static<T> void post(Activity activity, String url, HttpParams httpParams, final HttpRequestCallBack<T> callBack)
```



