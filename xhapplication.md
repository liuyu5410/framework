# XhApplication

---

项目中Application需要继承XhApplication，并且实现其中的抽象方法。

```java
/**
*
设置返回按钮
*
@return
*/
protected abstract int getBackIcon();
```

```java
/**
*获取标题文字颜色
*@return
*/
protected abstract int getTitleTextColor();
```

```java
/**
 * 网络请求的头，不可以有中文，不需要直接返回null就可以
 * @return
 */
protected abstract HttpHeaders getHttpHeaders();
```

```java
/**
 * 获取公共参数，支持中文，直接传不需要自己编码，不需要直接返回null就可以
 * @return
 */
protected abstract HttpParams getCommonHttpParams();
```



