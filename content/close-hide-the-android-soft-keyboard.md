# 关闭/隐藏安卓软键盘
[Close/hide the Android Soft Keyboard](https://stackoverflow.com/questions/1109022/close-hide-the-android-soft-keyboard)

___



> 1

你可以使用[InputMethodManager](http://developer.android.com/reference/android/view/inputmethod/InputMethodManager.html)通过调用[`hideSoftInputFromWindow`](http://developer.android.com/reference/android/view/inputmethod/InputMethodManager.html#hideSoftInputFromWindow%28android.os.IBinder,%20int%29)来强制关闭安卓的虚拟键盘，参数是当前聚焦的view的token

```java
// Check if no view has focus:
View view = this.getCurrentFocus();
if (view != null) {  
    InputMethodManager imm = (InputMethodManager)getSystemService(Context.INPUT_METHOD_SERVICE);
    imm.hideSoftInputFromWindow(view.getWindowToken(), 0);
}
```

有时候，你可能想传InputMethodManager.HIDE_IMPLICIT_ONLY作为第二个参数来保证你只会隐藏键盘。

如果是用kotlin:

```
context?.getSystemService(Context.INPUT_METHOD_SERVICE) as InputMethodManager
```

> 2

下面代码同样可以用来隐藏软键盘

```java
getWindow().setSoftInputMode(
    WindowManager.LayoutParams.SOFT_INPUT_STATE_ALWAYS_HIDDEN
);
```