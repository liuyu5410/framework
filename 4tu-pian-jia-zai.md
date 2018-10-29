# 图片加载

---

### 图片加载使用的类库是Glide

#### 1.加入相应的权限

```
 <uses-permission android:name="android.permission.INTERNET"/>
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
 <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" /> //要从本地文件夹或 DCIM 或图库中加载图片时用到
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" /> //将Glide的缓存存储到公有SD卡上时用到
```



