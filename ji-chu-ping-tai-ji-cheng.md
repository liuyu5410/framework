# **基础平台集成**

##### 基础平台目录结构如下

![](/assets/import.png)

#### XhApplication:

项目中Application需要继承XhApplication，并且实现其中的抽象方法。

```
/**
*
设置返回按钮
*
@return
*/
protected abstract int getBackIcon();
```

```
/**
*获取标题文字颜色
*@return
*/
protected abstract int getTitleTextColor();
```

```
/**
 * 网络请求的头，不可以有中文，不需要直接返回null就可以
 * @return
 */
protected abstract HttpHeaders getHttpHeaders();
```

```
/**
 * 获取公共参数，支持中文，直接传不需要自己编码，不需要直接返回null就可以
 * @return
 */
protected abstract HttpParams getCommonHttpParams();
```



