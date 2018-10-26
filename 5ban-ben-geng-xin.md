# 版本更新

---

#### 版本更新对UpdateApp进行了简单封装

```java
/* 版本更新
 * @param activity
 * @param params 接口需要的参数
 * @param url 接口地址
 * @param updateCallback  回调对象
 */
public static void update(Activity activity,Map<String, String> params, String url, UpdateCallback updateCallback)
```

#### 调用方法

这里要复写UpdateCallback中的parseJson方法，这个方法需要返回一个UpdateAppBean对象，所以在这个方法里根据自己版本更新接口返回的json协议对json进行解析，把数据解析到UpdateAppBean对象中，最后返回UpdateAppBean对象。

针对UpdateAppBean中的方法进行如下说明：

* ###### setUpdate\("Yes\No"\)设置是否有更新，如果为Yes代表有更新程序就会调用hasNewApp方法，如果为No代表没有更新程序就会调用noNewApp方法。
* ###### setNewVersion\(String\)设置新版本号，
* ###### setApkFileUrl\(String\)设置apk下载地址
* ###### setUpdateLog\(String\)设置更新日志
* ###### setConstraint\(String\)设置是否必须更新

```java
Map<String, String> params = new HashMap<String, String>();
params.put("device_type", "android");
params.put("apptype","1");
VersionUpdate.update(this,params,url,new UpdateCallback() {
                    /**
                     * 解析json,自定义协议,逻辑自己写
                     * 
                     * @param json 服务器返回的json
                     * @return UpdateAppBean
                     */
                    @Override
                    protected UpdateAppBean parseJson(String json) {
                        UpdateAppBean updateAppBean = new UpdateAppBean();
                        try {
                            JSONObject jsonObject = new JSONObject(json);
                            int errorCode = jsonObject.optInt("error_code");
                            if (errorCode == 0){
                                JSONObject data = jsonObject.getJSONObject("data");
                                updateAppBean.setUpdate("Yes")
                                        .setNewVersion(data.optString("version_code"))
                                        .setApkFileUrl(data.optString("link_url"))
                                        .setUpdateLog(data.optString("version_abstract"))
                                        .setConstraint("1".equals(data.optString("version_is_mustbeupdate")));
                            }else {
                                updateAppBean.setUpdate("No");
                            }
                        } catch (JSONException e) {
                            e.printStackTrace();
                        }
                        return updateAppBean;
                    }

                    @Override
                    protected void hasNewApp(UpdateAppBean updateApp, UpdateAppManager updateAppManager) {
                        //在此处可以自定义提示框，如果使用默认提示框不用复写hasNewApp方法
                        updateAppManager.showDialogFragment();
                    }

                    /**
                     * 网络请求之前
                     */
                    @Override
                    public void onBefore() {
                        CProgressDialogUtils.showProgressDialog(MainActivity.this);
                    }

                    /**
                     * 网路请求之后
                     */
                    @Override
                    public void onAfter() {
                        CProgressDialogUtils.cancelProgressDialog(MainActivity.this);
                    }

                    /**
                     * 没有新版本
                     */
                    @Override
                    public void noNewApp(String error) {
                        Toast.makeText(MainActivity.this, "没有新版本", Toast.LENGTH_SHORT).show();
                    }
                });
```

#### 参考

com.xh.framework.update.VersionUpdate

