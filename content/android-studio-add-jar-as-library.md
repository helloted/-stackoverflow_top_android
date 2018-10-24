# Android Studio添加一个jar库
[Android Studio: Add jar as library?](https://stackoverflow.com/questions/16608135/android-studio-add-jar-as-library)

___



> 1

这是我添加一个Gson jar的步骤

1. 把Gson jar添加到libs文件夹
2. 右击它然后点击'Add as library'
3. 确保`implementation files('libs/gson-2.2.4.jar')`在你的`build.gradle`文件里(或者`implementation fileTree(dir: 'libs', include: '*.jar')`)如果你使用了许多jar文件)
4. clean build

