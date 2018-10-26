# 网络框架

---

对应的类是com.xh.framework.net.HttpRequest.java

### POST请求

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

#### 调用方法

```java
HttpParams params = new HttpParams();
        params.put("telephone","13522757781");
        params.put("password","12345446");
HttpRequest.post(this, "http://ssqc.xiaohesoft.com/platformapi/index.php?act=user&op=login", params
                , new HttpRequestCallBack<UserBean>() {
                    @Override
                    public void onSuccess(UserBeanresult) {
                        //接口访问成功，并且error_code为0，会调用这个方法
                    }

                    @Override
                    public void onException(String msg) {
                        //网络请求异常会调用此方法
                    }

                    @Override
                    public void onError(int code, String msg) {
                        //接口访问成功，并且error_code不为0，会调用这个方法
                    }
                });
```



