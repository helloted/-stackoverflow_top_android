# 一行代码了事
1、获取Android唯一ID

```java
import android.provider.Settings.Secure;

private String android_id = Secure.getString(getContext().getContentResolver(),
                                                        Secure.ANDROID_ID); 
```

2、文本居中

```java
<TextView  
    android:layout_width="match_parent" 
    android:layout_height="match_parent" 
    android:gravity="center"
    android:text="@string/**yourtextstring**"
/>
```

 或者用代码：

```
textView.setGravity(Gravity.CENTER_VERTICAL | Gravity.CENTER_HORIZONTAL);
```

3、获取当前时间日期

```java
import java.util.Calendar

Date currentTime = Calendar.getInstance().getTime();
```

