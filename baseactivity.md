# AbstractActivity

---

项目中所有activity都继承AbstractActivity，其中集成了Toolbar，右滑关闭当前页面，设置标题文字。如果需要还可以进行再次封装。具体使用如下：

```java
public class ButtonActivity extends AbstractActivity{

    @BindView(R.id.tv)
    TextView tv;
    @BindView(R.id.btn)
    Button btn;

    @Override
    public int getLayout() {
        return R.layout.button_layout;
    }

    @Override
    public void init() {
        showBack(); //显示返回按钮 
        setCustomTitle(R.string.shop_cart); //设置标题
        setCustomTitle("购物车"); //设置标题
    }

    @OnClick({R.id.btn})
    public void onClick(View view){
        switch (view.getId()){
            case R.id.btn:
                String tmp = btn.getText().toString();
                tv.setText(tmp);
                break;
            default:
                break;
        }
    }
}
```



