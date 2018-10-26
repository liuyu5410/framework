# BaseActivity

---

项目中所有activity都继承BaseActivity，其中集成了Toolbar，右滑关闭当前页面，设置标题文字。如下：

```java
public class ButtonActivity extends BaseActivity {

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
        showBack();
        setCustomTitle(R.string.shop_cart);
        setCustomTitle("购物车");
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



