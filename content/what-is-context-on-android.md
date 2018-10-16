# 如何理解Android的Context?
[What is 'Context' on Android?](https://stackoverflow.com/questions/3572463/what-is-context-on-android)

___



> 1

顾名思义，上下文Context就是application/object当前的状态，让新创建的对象了解当前发生的事情。一般来说，可以通过它来获取其他部分(Activity或者package/application)的信息。

你可以通过以下方式来获取上下文context:`getApplicationContext()`, `getContext()`, `getBaseContext()` or `this` (当一个类继承自 `Context`, such 比如 Application, Activity, Service and IntentService classes)。

上下文Context的典型应用:

- 创建新对象：创建views, adapters, listeners:

  ```java
  TextView tv = new TextView(getContext());
  ListAdapter adapter = new SimpleCursorAdapter(getApplicationContext(), ...);
  ```

- 访问标准公共资源：Services 比如 LAYOUT_INFLATER_SERVICE, SharedPreferences:

- ```
  context.getSystemService(LAYOUT_INFLATER_SERVICE)
  getApplicationContext().getSharedPreferences(*name*, *mode*);
  ```

- 隐式地访问组件：content providers, broadcasts, intent

  ```
  getApplicationContext().getContentResolver().query(uri, ...);
  ```