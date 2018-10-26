# 版本更新

---

版本更新对APPUpdate进行了简单封装

```java
 * 版本更新
 * @param activity
 * @param params 接口需要的参数
 * @param url 接口地址
 * @param updateCallback  回调对象
 */
public static void update(Activity activity,Map<String, String> params, String url, UpdateCallback updateCallback)
```

调用方法

```java
Map<String, String> params = new HashMap<String, String>();
params.put("device_type", "android");
params.put("apptype","1");
VersionUpdate.update(this,params,url,new UpdateCallback() {
                    /**
                     * 解析json,自定义协议
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



