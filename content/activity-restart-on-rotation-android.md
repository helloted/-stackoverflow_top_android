# 旋转时Activity Restart?
[Activity restart on rotation Android](https://stackoverflow.com/questions/456211/activity-restart-on-rotation-android)

当我旋转机器的时候，Activity会restarted(OnCreate被再次调用)，然而，因为我在OnCreate方法里做了很多初始化，但我并不想再次初始化，我应该怎么做？

___



> 1

使用**Application Class**

根据你的需求，你可以考虑创建一个新的类继承自Application，然后把你的初始化代码移动到OnCreate方法里

```
public class MyApplicationClass extends Application {
  @Override
  public void onCreate() {
    super.onCreate();
    // TODO Put your application initialization code here.
  }
}
```

application类里的onCreate只会在整个应用被创建的时候被调用，所以旋转机器或者键盘移动不会触发它。

把这个类的实例拓展成一个单例，然后将整个程序相关的变量在里面初始化，getter、setter，是一个很好的用途。

注意，你需要在*manifest*里对这个类进行注册

```
<application
    android:name="com.you.yourapp.MyApplicationClass"
```