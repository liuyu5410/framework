# SQLite

---

基础框架中对SQLiteOpenHelper进行了封装，XhSQLite是封装后的新类。

#### 1.创建数据库

```java
List<Object> objectList = new ArrayList<>();
objectList.add(new AvatarBean());
objectList.add(new CastBean());
objectList.add(new MovieBean());
objectList.add(new RatingBean());
XhSQLite.init(this,new MyCallBack(),1,"test.db",objectList);
```



