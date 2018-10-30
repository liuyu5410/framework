# **基础平台集成**

---

##### 集成步骤：

* 点击File-&gt;New-&gt;Import Module...选择基础平台项目。
* 在settings.gradle中添加基础平台（include ':app', ':framework'）
* 在app下的build.gradle中把基础平台作为类库引用（implementation project\(':framework'\)）

##### 基础平台目录结构如下

![](/assets/import.png)

