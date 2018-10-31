# 网络框架

---

### 说明：根据自己项目接口情况进行代码编写

#### 1.返回结果是对象

* 例如是一个LoginBean，在调用方法时直接使用OkGo.&lt;XhResponse&lt;LoginBean&gt;&gt;post加上相应的方法即可。
* 如果请求成功会调用EncryptCallback中的onSuccess方法，用LoginBean loginBean = response.body\(\).data即可获取到LoginBean的对象
* 请求成功返回错误结果和请求失败都会直接调用EncryptCallback中的onError方法，基础平台会对错误结果进行统一处理。

#### 2.返回结果是列表

* 例如是一个LoginBean的列表，在调用方法时直接使用OkGo.&lt;XhResponse&lt;List&lt;LoginBean&gt;&gt;&gt;post加上相应的方法即可。
* 如果请求成功会调用EncryptCallback中的onSuccess方法，用List&lt;LoginBean&gt; loginBeanList = response.body\(\).data即可获取到LoginBean的列表。

#### 3.返回结果只有error\_code和msg

* 在调用方法时直接使用OkGo.&lt;XhResponse&lt;这里可以放Object、String或者其它参数&gt;&gt;&gt;post。
* 在请求成功后，如果需要显示msg信息就用response.body\(\).msg解析，如果不需要显示msg信息，直接在onSuccess中进行逻辑操作。



### POST请求

```java
//参数
HttpParams params = new HttpParams();
params.put("telephone","13522757781");
params.put("password","1234596");
OkGo.<XhResponse<LoginBean>>post("http://ssqc.xiaohesoft.com/platformapi/index.php?act=user&op=login")//接口地址
                .tag(this) //设置tag
                .params(params) //添加参数
                .execute(new EncryptCallback<XhResponse<LoginBean>>(this) {
                    @Override
                    public void onSuccess(Response<XhResponse<LoginBean>> response) {
                        //请求成功
                        LoginBean loginBean = response.body().data;
                    }
                });
```

### GET请求

```java
//参数
HttpParams params = new HttpParams();
params.put("telephone","13522757781");
params.put("password","1234596");
OkGo.<XhResponse<LoginBean>>get("http://ssqc.xiaohesoft.com/platformapi/index.php?act=user&op=login")//接口地址
                .tag(this) //设置tag
                .params(params) //添加参数
                .execute(new EncryptCallback<XhResponse<LoginBean>>(this) {
                    @Override
                    public void onSuccess(Response<XhResponse<LoginBean>> response) {
                        //请求成功
                        LoginBean loginBean = response.body().data;
                    }
                });
```

### 上传文件

```java
 //参数
 HttpParams params = new HttpParams();
 params.put("token","safasdfasfweeoi0923");
 List<File> fileList = new ArrayList<>();
 OkGo.<XhResponse<String>>post("http://ssqc.xiaohesoft.com/platformapi/index.php?act=seller&op=imageupload")//接口地址
                .tag(this) //设置tag
                .params(params)//添加参数
                .addFileParams("file",fileList) //添加文件
                .execute(new EncryptCallback<XhResponse<String>>(this) {
                    @Override
                    public void onSuccess(Response<XhResponse<String>> response) {
                        //上传成功
                    }
                });
```

#### 



