# 一行代码了事
1、获取Android唯一ID

```java
import android.provider.Settings.Secure;

private String android_id = Secure.getString(getContext().getContentResolver(),
                                                        Secure.ANDROID_ID); 
```



