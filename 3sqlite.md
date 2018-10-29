# SQLite

---

基础框架中对SQLiteOpenHelper进行了封装，XhSQLite是封装后的新类。封装之后JavaBean的类名作为数据库中的表名

#### 1.创建数据库

创建一个Object类型的List数组，并且实例化。

将JavaBean实例化的对象添加到List中

调用init方法传入需要参数进行数据库创建操作

```java
List<Object> objectList = new ArrayList<>();
objectList.add(new AvatarBean());
objectList.add(new CastBean());
objectList.add(new MovieBean());
objectList.add(new RatingBean());
XhSQLite.init(this,new MyCallBack(),1,"test.db",objectList);
```



