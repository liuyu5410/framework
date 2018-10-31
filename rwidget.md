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

| 属性 | 说明 |
| :--- | :--- |
| corner\_radius | 圆角 四周 |
| corner\_radius\_top\_left | 圆角 左上 |
| corner\_radius\_top\_right | 圆角 右上 |
| corner\_radius\_bottom\_left | 圆角 左下 |
| corner\_radius\_bottom\_right | 圆角 右下 |
| border\_dash\_width | 虚线边框 宽度 |
| border\_dash\_gap | 虚线边框 间隔 |
| border\_width\_normal | 边框宽度 默认 |
| border\_width\_pressed | 边框宽度 按下 |
| border\_width\_unable | 边框宽度 不可点击 |
| border\_color\_normal | 边框颜色 默认 |
| border\_color\_pressed | 边框颜色 按下 |
| border\_color\_unable | 边框颜色 不可点击 |
| background\_normal | 背景颜色 默认 |
| background\_pressed | 背景颜色 按下 |
| background\_unable | 背景颜色 不可点击 |
| text\_color\_normal | 文字颜色 默认 |
| text\_color\_pressed | 文字颜色 按下 |
| text\_color\_unable | 文字颜色 不可点击 |
| icon\_src\_normal | drawable icon 默认 |
| icon\_src\_pressed | drawable icon 按下 |
| icon\_src\_unable | drawable icon 不可点击 |
| icon\_height | drawable icon 高 |
| icon\_width | drawable icon 宽 |
| icon\_direction | drawable icon 位置{left,top,right,bottom} |
| text\_typeface | 字体样式 |



