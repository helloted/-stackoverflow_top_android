# gravity和layout_gravity区别？
[Difference between gravity and layout_gravity on Android](https://stackoverflow.com/questions/3482742/difference-between-gravity-and-layout-gravity-on-android)

___



> 1

可以从名字区分：

- `android:gravity` 用以摆放View的内容(比如subviews)在View当中的位置
- `android:layout_gravity` 用以摆放 `View` 或者 `Layout` 在他们父对象中的位置.

![img](/images/02.png)

