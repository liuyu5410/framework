# RWidgetHelper

---

##### 继承基础控件 1.直接在控件实现selector，shape，gradient功能 2.无需另写xml实现圆形，圆角，渐变以及各个state状态背景/边框/文字颜色

其中包含RTextView\(TextView\)，RImageView\(ImageView\)，REditText\(EditText\)，RView\(View\)，RLinearlayout\(Linealayout\)

以RTextView为例

```css
<com.ruffian.library.widget.RTextView
    android:id="@+id/text6"
    android:layout_width="150dp"
    android:layout_height="100dp"
    android:layout_marginLeft="10dp"
    android:clickable="true"
    android:gravity="center"
    android:paddingTop="10dp"
    android:text="背景/边框/文字/图片\n变色"
    android:textColor="@android:color/white"
    rtv:background_normal="@color/colorPrimary"
    rtv:background_pressed="#FF450F21"
    rtv:border_color_normal="@color/colorAccent"
    rtv:border_color_pressed="@color/colorPrimary"
    rtv:border_width_normal="3dp"
    rtv:corner_radius="10dp"
    rtv:icon_direction="top"
    rtv:icon_height="30dp"
    rtv:icon_src_normal="@mipmap/icon_phone_normal"
    rtv:icon_src_pressed="@mipmap/icon_phone_pressed"
    rtv:icon_width="30dp"
    rtv:text_color_pressed="@color/colorPrimary" />
```



