# 保存Activity State
[Saving Android Activity state using Save Instance State](https://stackoverflow.com/questions/151777/saving-android-activity-state-using-save-instance-state)

___



> 1

你需要重写`onSaveInstanceState(Bundle savedInstanceState)`然后把你需要保存的值存到Bundle里，就像下面这样:

```java
@Override
public void onSaveInstanceState(Bundle savedInstanceState) {
  super.onSaveInstanceState(savedInstanceState);
  // Save UI state changes to the savedInstanceState.
  // This bundle will be passed to onCreate if the process is
  // killed and restarted.
  savedInstanceState.putBoolean("MyBoolean", true);
  savedInstanceState.putDouble("myDouble", 1.9);
  savedInstanceState.putInt("MyInt", 1);
  savedInstanceState.putString("MyString", "Welcome back to Android");
  // etc.
}
```

Bundle本质上是一个map可以用来存储键值对，你可以通过在`onCreate()` 或者重写 `onRestoreInstanceState()`来得到值：

```java
@Override
public void onRestoreInstanceState(Bundle savedInstanceState) {
  super.onRestoreInstanceState(savedInstanceState);
  // Restore UI state from the savedInstanceState.
  // This bundle has also been passed to onCreate.
  boolean myBoolean = savedInstanceState.getBoolean("MyBoolean");
  double myDouble = savedInstanceState.getDouble("myDouble");
  int myInt = savedInstanceState.getInt("MyInt");
  String myString = savedInstanceState.getString("MyString");
}
```