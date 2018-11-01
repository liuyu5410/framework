# 权限管理

---

```java
Acp.getInstance(this).request(new AcpOptions.Builder()
                .setPermissions(Manifest.permission.CALL_PHONE)
                .build(), new AcpListener() {
            @Override
            public void onGranted() {
                // Todo 允许权限
            }

            @Override
            public void onDenied(List<String> permissions) {
                // Todo 不允许权限
            }
        });
```



