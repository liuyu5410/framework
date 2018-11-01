# 开发规范

---

### 1.AS 规范

1. 尽量使用最新的稳定版的 IDE 进行开发；
2. 编码格式统一为 **UTF-8**；
3. 编辑完 .java、.xml 等文件后一定要 **格式化，格式化，格式化**（如果团队有公共的样式包，那就遵循它，否则统一使用 AS 默认模板即可）；
4. 删除多余的 import，减少警告出现，可利用 AS 的 Optimize Imports（Settings -&gt; Keymap -&gt; Optimize Imports）快捷键；

### 2.命名规范

代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。正确的英文拼写和语法可以让阅读者易于理解，避免歧义。

#### 2.1包名

包名全部小写，连续的单词只是简单地连接起来，不使用下划线，采用反域名命名规则，全部使用小写字母。一级包名是顶级域名，通常为 com、edu、gov、net、org 等，二级包名为公司名，三级包名根据应用进行命名，后面就是对包名的划分了。一般编写按照mvc模式设计。

#### 2.2类名

* 类名都以 UpperCamelCase 风格编写。
* 类名通常是名词或名词短语，接口名称有时可能是形容词或形容词短语。现在还没有特定的规则或行之有效的约定来命名注解类型。
* 名词，采用大驼峰命名法，尽量避免缩写，除非该缩写是众所周知的， 比如 HTML、URL，如果类名称中包含单词缩写，则单词缩写的每个字母均应大写。

| 类 | 描述 | 例如 |
| :--- | :--- | :--- |
| `Activity` 类 | `Activity` 为后缀标识 | 欢迎页面类 `WelcomeActivity` |
| `Adapter` 类 | `Adapter` 为后缀标识 | 新闻详情适配器 `NewsDetailAdapter` |
| 解析类 | `Parser` 为后缀标识 | 首页解析类 `HomePosterParser` |
| 工具方法类 | `Utils` 或 `Manager` 为后缀标识 | 线程池管理类：`ThreadPoolManager` 日志工具类：`LogUtils`（`Logger` 也可） 打印工具类：`PrinterUtils` |
| `Service` 类 | 以 `Service` 为后缀标识 | 时间服务 `TimeService` |
| `BroadcastReceiver` 类 | 以 `Receiver` 为后缀标识 | 推送接收 `JPushReceiver` |
| `ContentProvider` 类 | 以 `Provider` 为后缀标识 | `ShareProvider` |
| 自定义的共享基础类 | 以 `Base` 开头 | `BaseActivity`, `BaseFragment` |

测试类的命名以它要测试的类的名称开始，以 Test 结束。例如：HashTest 或 HashIntegrationTest。

接口（interface）：命名规则与类一样采用大驼峰命名法。

#### 2.3方法名

* 方法名都以 lowerCamelCase 风格编写。
* 方法名通常是动词或动词短语。

| 方法 | 说明 |
| :--- | :--- |
| `initXX()` | 初始化相关方法，使用 init 为前缀标识，如初始化布局 `initView()` |
| `isXX()`, `checkXX()` | 方法返回值为 boolean 型的请使用 is/check 为前缀标识 |
| `getXX()` | 返回某个值的方法，使用 get 为前缀标识 |
| `setXX()` | 设置某个属性值 |
| `handleXX()`, `processXX()` | 对数据进行处理的方法 |
| `displayXX()`, `showXX()` | 弹出提示框和提示信息，使用 display/show 为前缀标识 |
| `updateXX()` | 更新数据 |
| `saveXX()`, `insertXX()` | 保存或插入数据 |
| `resetXX()` | 重置数据 |
| `clearXX()` | 清除数据 |
| `removeXX()`, `deleteXX()` | 移除数据或者视图等，如 `removeView()` |
| `drawXX()` | 绘制数据或效果相关的，使用 draw 前缀标识 |

#### 2.4常量命名

常量名命名模式为 CONSTANT\_CASE，全部字母大写，用下划线分隔单词。

#### 2.5变量命名

变量命名以`lowerCamelCase`风格为主。例如String firstName。尽量避免使用小写字母加下划线。

#### 2.6参数名

参数名以 lowerCamelCase 风格编写，参数应该避免用单个字符命名。

#### 2.7资源文件命名

资源文件命名用小写字母加下划线

### 3代码样式规范

#### 3.1使用标准大括号样式

左大括号不单独占一行，与其前面的代码位于同一行：

需要在条件语句周围添加大括号。

```java
class MyClass {
    int func() {
        if (something) {
            // ...
        } else if (somethingElse) {
            // ...
        } else {
            // ...
        }
    }
}
```

#### 3.2编写简短方法

在可行的情况下，尽量编写短小精炼的方法。我们了解，有些情况下较长的方法是恰当的，因此对方法的代码长度没有做出硬性限制。如果某个方法的代码超出 40 行，请考虑是否可以在不破坏程序结构的前提下对其拆解。

#### 3.3类成员的顺序

这并没有唯一的正确解决方案，但如果都使用一致的顺序将会提高代码的可读性，推荐使用如下排序：

1. 常量
2. 字段
3. 构造函数
4. 重写函数和回调
5. 公有函数
6. 私有函数
7. 内部类或接口

   例如：

```java
public class MainActivity extends Activity {
    private static final String TAG = MainActivity.class.getSimpleName();
    private String mTitle;
    private TextView mTextViewTitle;

    @Override
    public void onCreate() { ...}

    public void setTitle(String title) {
        mTitle = title;
    }

    private void setUpView() { ...}

    static class AnInnerClass {
    }

}
```

#### 3.4函数参数的排序

* 在 Android 开发过程中，Context 在函数参数中是再常见不过的了，我们最好把 Context 作为其第一个参数。 
* 正相反，我们把回调接口应该作为其最后一个参数。

```java
// Context always goes first
public User loadUser(Context context, int userId);
// Callbacks always go last 
public void loadUserAsync(Context context, int userId, UserCallback callback);
```

#### 3.5 Fragment传参

启动相关 Fragment 在其内部输入 newInstance 即可，如下所示：

```java
public static FragmentState newInstance(User user) {
    Bundle args = new Bundle();
    args.putParcelable(ARGUMENT_USER, user);
    FragmentState fragment = new FragmentState();
    fragment.setArguments(args);
    return fragment;
}
```

#### 3.6操作符的换行

除赋值操作符之外，我们把换行符放在操作符之前，例如：

```java
int longName = anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne
        + theFinalOne;
```

赋值操作符的换行我们放在其后，例如：

```java
int longName =
        anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne + theFinalOne;
```

#### 3.7多参数的换行

当一个方法有很多参数或者参数很长的时候，我们应该在每个 , 后面进行换行。 比如：

```java
loadPicture(context, "https://blankj.com/images/avatar.jpg", ivAvatar, "Avatar of the user", clickListener);
```

我们应该使用如下规则：

```java
loadPicture(context,
        "https://blankj.com/images/avatar.jpg",
        ivAvatar,
        "Avatar of the user",
        clickListener);
```

### 4注释规范

#### 4.1类注释

每个类都应该有作者名，对自己的代码负责

```java
/**
 * @author : LiuYu
 * @time : 2018/11/01
 * @desc :
 */
public class TestActivity extends AppCompatActivity {
}
```

具体可以在 AS 中自己配制，进入 Settings -&gt; Editor -&gt; File and Code Templates -&gt; Includes -&gt; File Header，输入

```java
/**
 *     @author  : ${USER}
 *     @time    : ${YEAR}/${MONTH}/${DAY}
 *     @desc    :
 */
```

这样可以在每次新建类时自动添加头注释

#### 4.2方法注释

一个成员方法（包括自定义成员方法、覆盖方法、属性方法）的方法头都必须做方法头注释，在方法前一行输入 /\*\* + 回车 或者设置 Fix doc comment（Settings -&gt; Keymap -&gt; Fix doc comment）快捷键，AS 便会帮你生成模板，我们只需要补全参数即可，如下所示。

```java
 /**
  * bitmap 转 byteArr
  * @param bitmap bitmap 对象
  * @param format 格式
  * @return 字节数组
  */
 public static byte[] bitmap2Bytes(Bitmap bitmap, Bitmap.CompressFormat format) {
    if (bitmap == null) {return null;}
    ByteArrayOutputStream baos = new ByteArrayOutputStream();
    bitmap.compress(format, 100, baos);
    return baos.toByteArray();
 }
```

#### 4.3块注释

块注释与其周围的代码在同一缩进级别。它们可以是 /\* ... \*/ 风格，也可以是 // ... 风格（//后最好带一个空格）。对于多行的 /\* ... \*/ 注释，后续行必须从 \* 开始， 并且与前一行的 \* 对齐。以下示例注释都是 OK 的。

```java
/*
 * This is
 * okay.
 */

// And so
// is this.

/* Or you can
* even do this. */
```

#### 4.4其他一些注释

 AS 已帮你集成了一些注释模板，我们只需要直接使用即可，在代码中输入 todo、fixme 等这些注释模板，回车后便会出现如下注释。



