# SQLite

---

基础框架中对SQLiteOpenHelper进行了封装，XhSQLite是封装后的新类。封装之后的XhSQLite和JavaBean配合使用，会将JavaBean的类名（小写）作为数据库中的表名，数据库名需要在初始化时传入。在创建表时，会自动生成\_ID字段作为主键，并且自增。

#### 1.创建数据库

* 创建一个Object类型的List数组，并且实例化。
* 将JavaBean实例化的对象添加到List中
* 调用init方法传入需要参数进行数据库创建操作

```java
List<Object> objectList = new ArrayList<>();
objectList.add(new AvatarBean());
objectList.add(new CastBean());
objectList.add(new MovieBean());
objectList.add(new RatingBean());
XhSQLite.init(this,new MyCallBack(),1,"test.db",objectList);
```

查看数据库中表创建情况如下，通过查看数据库中的表发现，JavaBean类名的小写字母作为了表名。

![](/assets/db_test.png)

#### 2.插入数据

##### 2.1出入单条数据

```java
 AvatarBean avatarBean = new AvatarBean();
 avatarBean.setLarge("114234");
 avatarBean.setMedium("ooiiew");
 avatarBean.setSmall("oos");
 XhSQLite.insert(avatarBean);
```

##### 2.2插入多条数据

```java
 List<AvatarBean> avatarBeanList = new ArrayList<>();
 AvatarBean avatarBean = new AvatarBean();
 avatarBean.setLarge("114234");
 avatarBean.setMedium("ooiiew");
 avatarBean.setSmall("oos");
 AvatarBean avatarBean2 = new AvatarBean();
 avatarBean.setLarge("1");
 avatarBean.setMedium("3ds");
 avatarBean.setSmall("odfadsfos");
 XhSQLite.insert(avatarBeanList);
```

#### 3.查询数据

##### 3.1查询某表中的全部数据

```java
List<AvatarBean> avatarList = XhSQLite.query(new AvatarBean());
```

##### 3.2按条件查找

```java
List<AvatarBean> avatarList = XhSQLite.query(new AvatarBean(),"select * from avatarbean where _ID = ?",new String[]{"1"});
```

#### 4.更新数据

```java
AvatarBean avatarBean = new AvatarBean();
avatarBean.setLarge("321312");
avatarBean.setMedium("df2343");
avatarBean.setSmall("dsiewwo");
XhSQLite.update(avatarBean,"_ID = ?",new String[]{"1"});
```

更新前

![](/assets/db_update.png)

更新后

![](/assets/update_db.png)

#### 5.删除数据

5.1删除全部数据

```java
XhSQLite.deleteFrom(new AvatarBean());
```



