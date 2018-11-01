# ButterKnife（黄油刀）

---

ButterKnife是一个专注于Android系统的View注入框架,以前总是要写很多findViewById来找到View对象，有了ButterKnife可以很轻松的省去这些步骤。是大神JakeWharton的力作，目前使用很广。最重要的一点，使用ButterKnife对性能基本没有损失，因为ButterKnife用到的注解并不是在运行时反射的，而是在编译的时候生成新的class。项目集成起来也是特别方便，使用起来也是特别简单。

**在Activity中绑定ButterKnife：**

由于每次都要在Activity中的onCreate绑定Activity，所以个人建议写一个BaseActivity完成绑定，子类继承即可。绑定Activity 必须在setContentView之后。使用ButterKnife.bind\(this\)进行绑定。代码如下：

```java
 public class MainActivity extends AppCompatActivity {
        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main); //绑定初始化ButterKnife ButterKnife.bind(this); 
        }
    }
```

**在Fragment中绑定ButterKnife：**

```java
    public class ButterknifeFragment extends Fragment {
        private Unbinder unbinder;

        @Override
        public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
            View view = inflater.inflate(R.layout.fragment, container, false);
            //返回一个Unbinder值（进行解绑），注意这里的this不能使用getActivity()
            unbinder = ButterKnife.bind(this, view);
            return view;
        }

        /**
         * onDestroyView中进行解绑操作
         */
        @Override
        public void onDestroyView() {
            super.onDestroyView();
            unbinder.unbind();
        }
    }
```

**在Adapter中绑定ButterKnife：**

在Adapter的ViewHolder中使用，将ViewHolder加一个构造方法，在new ViewHolder的时候把view传递进去。使用ButterKnife.bind\(this, view\)进行绑定，代码如下：

```java
    public class MyAdapter extends BaseAdapter {
        @Override
        public View getView(int position, View view, ViewGroup parent) {
            ViewHolder holder;
            if (view != null) {
                holder = (ViewHolder) view.getTag();
            } else {
                view = inflater.inflate(R.layout.testlayout, parent, false);
                holder = new ViewHolder(view);
                view.setTag(holder);
            }
            holder.name.setText("Donkor");
            holder.job.setText("Android"); // etc...
            return view;
        }

        static class ViewHolder {
            @BindView(R.id.title)
            TextView name;
            @BindView(R.id.job)
            TextView job;

            public ViewHolder(View view) {
                ButterKnife.bind(this, view);
            }
        }
    }
```

**ButterKnife的基本使用**

1. **绑定View：**

 控件id 注解： @BindView（）

```java
@BindView( R2.id.button)  
public Button button; 
```



