# Android Studio中的Gradle
[What is Gradle in Android Studio?](https://stackoverflow.com/questions/16754643/what-is-gradle-in-android-studio)

___



> 1

Gradle是一个构建系统

在Android Studio之前，你使用Eclipse进行开发，而且很可能，您不知道如何在没有Eclipse的情况下构建Android APK。

您可以在命令行上执行此操作，但您必须了解SDK中每个工具（dx，aapt）的功能。 Eclipse通过为我们提供他们自己的构建系统，从这些低级但重要的基础细节中拯救了我们所有人。

构建系统自动获取所有源文件（.java或.xml），然后应用适当的工具（例如，获取java类文件并将它们转换为dex文件），并将它们全部组合成一个压缩文件：APK。

Gradle是另一个构建系统，它从其他构建系统中获取最佳功能并将它们合并为一个。它是基于它们的缺点而改进的。它是一个基于JVM的构建系统，这意味着您可以用Java编写自己的脚本，Android Studio可以使用它。

关于gradle的一个很酷的事情是它是一个基于插件的系统。这意味着如果你有自己的编程语言，并且想要从源代码中自动完成构建一些包（如JAR for Java的输出）的任务，那么你可以用Java或Groovy（或Kotlin，见这里）编写一个完整的插件，将它分发给世界其他地方。

谷歌为何使用它？
Google看到了市场上最先进的构建系统之一，你可以编写自己的脚本，几乎没有学习曲线，也无需学习Groovy或任何其他新语言。 所以他们为Gradle编写了Android插件。

您肯定已在项目中看到build.gradle文件。 在这里，您可以编写脚本来自动执行任务。 您在这些文件中看到的代码是Groovy代码。 如果你编写System.out.println（“Hello Gradle！”）; 然后它将在您的控制台上打印。

你可以在构建脚本中做什么？
一个简单的例子是，在实际构建过程发生之前，您必须将一些文件从一个目录复制到另一个目录。 Gradle构建脚本可以执行此操作。



> 2

Gradle是在Android Studio上运行的构建系统。

其他语言中的例子:

- [Ant](http://ant.apache.org/) and [Maven](https://maven.apache.org/) of **Java**
- [Rake](https://github.com/ruby/rake) of **Ruby**
- [A-A-P](http://www.a-a-p.org/) of **C**
- [NAnt](http://nant.sourceforge.net/) of **.NET**
- [Make](https://www.gnu.org/software/make/) in **Linux**