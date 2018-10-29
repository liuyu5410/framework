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

#### 2.使用方法

```java
Glide.with(fragment) //Fragment和Activity都可以
  .load(url)
  .placeholder(R.drawable.placeholder) //占位符，不是必须
  .error(R.drawable.error) //错误符，不是必须
  .into(view);
```

详细信息可以参考[Glide](https://muyangmin.github.io/glide-docs-cn/doc/placeholders.html)

