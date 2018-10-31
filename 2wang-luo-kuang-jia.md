# 网络框架

---

### POST请求

```java
//参数
HttpParams params = new HttpParams();
params.put("telephone","13522757781");
params.put("password","1234596");
OkGo.<LzyResponse<LoginBean>>post("http://ssqc.xiaohesoft.com/platformapi/index.php?act=user&op=login")//接口地址
                .tag(this) //设置tag
                .params(params) //添加参数
                .execute(new EncryptCallback<LzyResponse<LoginBean>>(this) {
                    @Override
                    public void onSuccess(Response<LzyResponse<LoginBean>> response) {
                        //请求成功
                        LoginBean loginBean = response.body().data;
                    }
                });
```

#### 调用方法

```java
HttpParams params = new HttpParams();
        params.put("telephone","13522757781");
        params.put("password","12345446");
HttpRequest.post(this, "http://ssqc.xiaohesoft.com/platformapi/index.php?act=user&op=login", params
                , new HttpRequestCallBack<UserBean>() {
                    @Override
                    public void onSuccess(UserBean result) {
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

### GET请求

```java
/**
 * get请求，不带加载框
 *  @param activity activity
 * @param url url
 * @param httpParams 参数
 * @param callBack 回调接口
 * @param <T> 泛型,如果接口返回的是对象，直接传Bean，如果接口返回的是list,传List<Bean>
 */
 public static<T> void get(Activity activity, String url, HttpParams httpParams, final HttpRequestCallBack<T> callBack){
```

#### 调用方法

同POST请求

### 上传文件

```java
/**
 * 上传文件（多张），不带加载框
 * @param activity
 * @param url
 * @param params 文本参数
 * @param fileList 文件
 * @param callBack
 * @param <T> 泛型,如果接口返回的是对象，直接传Bean，如果接口返回的是list,传List<Bean>
 */
 public static<T> void uploadFile(Activity activity, String url, HttpParams params, List<File> fileList, final HttpRequestCallBack<T> callBack)
```

#### 调用方法

同POST请求方式一样，调用这个方法需要传文件list参数

