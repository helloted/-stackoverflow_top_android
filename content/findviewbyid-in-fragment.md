# Fragment里的findViewById？
[findViewById in Fragment](https://stackoverflow.com/questions/6495898/findviewbyid-in-fragment)

我在Fragment里创建了一个ImageView，并且在Frament的XML里有refer。然而，只有在我继承自Activity里的类里才可以使用findViewById方法，是否有什么方式在Fragment也可以？就想下面一样

```java
public class TestClass extends Fragment {
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        ImageView imageView = (ImageView)findViewById(R.id.my_image);
        return inflater.inflate(R.layout.testclassfragment, container, false);
    }
}
```

findViewById方法会报错提示undefined

___



> 1

在onViewCreated方法的实现里使用getView()，这样会返回frament的root View，你就可以调用`findViewById()`了

```java
@Override
public void onViewCreated(View view, @Nullable Bundle savedInstanceState) {
    ImageView imageView = (ImageView) getView().findViewById(R.id.foo);
    // or  (ImageView) view.findViewById(R.id.foo); 
```

`getView()` 只有在 `onCreateView()`可以使用，你不能在onCreate()或onCreateView() methods** of the fragment .