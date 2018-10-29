# 权限管理

---

```java
PermissionUtil.permission(this, new AcpListener() {
            @Override
            public void onGranted() {
                //允许权限，在这里进行逻辑操作
            }

            @Override
            public void onDenied(List<String> permissions) {
                //不允许权限，在这里进行逻辑操作
            }
        }, Manifest.permission.WRITE_EXTERNAL_STORAGE,Manifest.permission.CAMERA, Manifest.permission.SEND_SMS);
```



