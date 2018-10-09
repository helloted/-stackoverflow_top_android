# 获取屏幕尺寸？
[Get screen dimensions in pixels](https://stackoverflow.com/questions/1016896/get-screen-dimensions-in-pixels)

如何在mainActivity里获取屏幕宽度和屏幕高度？

___



> 1

你可以使用getSize来获取像素尺寸：

```java
Display display = getWindowManager().getDefaultDisplay();
Point size = new Point();
display.getSize(size);
int width = size.x;
int height = size.y;
```

如果你的代码不是在一个Activity内，你可以获取到默认的Display通过WINDOW_SERVICE:

```java
WindowManager wm = (WindowManager) context.getSystemService(Context.WINDOW_SERVICE);
Display display = wm.getDefaultDisplay();
```

在API13之前你可以用下面这个方法，不过已经被废弃了：

```java
Display display = getWindowManager().getDefaultDisplay(); 
int width = display.getWidth();  // deprecated
int height = display.getHeight();  // deprecated
```

但是有新的方法就是：

```java
DisplayMetrics metrics = new DisplayMetrics();
getWindowManager().getDefaultDisplay().getMetrics(metrics);

int height = metrics.heightPixels;
int width = metrics.widthPixels;
```