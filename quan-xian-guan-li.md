# 权限管理

---

```java
PermissionUtil.permission(this, new AcpListener() {
            @Override
            public void onGranted() {
                XhLog.d("同意");
            }

            @Override
            public void onDenied(List<String> permissions) {
                XhLog.d(permissions.toString()+"被拒绝");
            }
        }, Manifest.permission.WRITE_EXTERNAL_STORAGE,Manifest.permission.CAMERA, Manifest.permission.SEND_SMS);
```



