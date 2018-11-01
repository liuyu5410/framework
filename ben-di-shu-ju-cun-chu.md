# 本地数据存储

---

### 1FileCachUtil

##### 设置缓存方法

```java
    /**
     * 缓存数据到文件
     * @param context context
     * @param content 存储内容
     * @param cacheFileName 文件名
     * @param mode  模式
     */
    public static void setCache(Context context, String content, String cacheFileName, int mode) {
        FileOutputStream fos = null;
        try {
            //打开文件输出流，接收参数是文件名和模式
            fos = context.openFileOutput(cacheFileName, mode);
            fos.write(content.getBytes());
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fos != null) {
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

```

```java
    /**
     * 缓存数据到文件
     * @param context
     * @param content 存取数据
     * @param cacheFileName 存取文件
     * @param mode 模式
     */
    public static void setCache(Context context,byte[] content,String cacheFileName, int mode) {
        FileOutputStream fos = null;
        try {
            //打开文件输出流，接收参数是文件名和模式
            fos = context.openFileOutput(cacheFileName, mode);
            fos.write(content);
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fos != null) {
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
```

##### 从缓存中去数据

```
    /**
     * 读取缓存，返回字符串
     * @param context
     * @param cacheFileName 文件名
     * @return
     */
    public static String getCache(Context context, String cacheFileName) {
        FileInputStream fis = null;
        StringBuffer sBuf = new StringBuffer();
        try {
            fis = context.openFileInput(cacheFileName);
            int len = 0;
            byte[] buf = new byte[1024];
            while ((len = fis.read(buf)) != -1) {
                sBuf.append(new String(buf, 0, len));
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
        if (sBuf != null) {
            return sBuf.toString();
        }
        return null;
    }
```

### 2SharedPreferencesUtil

对SharedPreferences的封装，包含了String,int,float,long,boolean的put、get方法和getAll



