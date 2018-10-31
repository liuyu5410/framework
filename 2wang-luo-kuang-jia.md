# 网络框架

---

### 说明

如果请求结果是一个对象，例如是一个LoginBean的，在调用方法时直接使用OkGo.&lt;XhResponse&lt;LoginBean&gt;&gt;post

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
                    public void onSuccess(XhResponse<XhResponse<String>> response) {
                        //上传成功
                    }
                });
```

#### 



