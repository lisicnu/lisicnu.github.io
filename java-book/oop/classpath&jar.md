
## classPath
`classpath`是JVM用到的一个环境变量，它用来指示JVM如何搜索`class`。因为Java是编译型语言，源码文件是.java，而编译后的.class文件才是真正可以被JVM执行的字节码。    

因此，JVM需要知道，如果要加载一个abc.xyz.Hello的类，应该去哪搜索对应的Hello.class文件。所以，`classpath`就是一组目录的集合，它设置的搜索路径与操作系统相关。  
  
例如，在Windows系统上，用;分隔，带空格的目录用""括起来，可能长这样： 
``` 
C:\work\project1\bin;C:\shared;"D:\My Documents\project1\bin" 
```

现在我们假设classpath是  .; C:\work\project1\bin;C:\shared，  
当JVM在加载abc.xyz.Hello这个类时，会依次查找：
```
<当前目录>\abc\xyz\Hello.class
C:\work\project1\bin\abc\xyz\Hello.class
C:\shared\abc\xyz\Hello.class  
```

注意到 .代表当前目录。如果JVM在某个路径下找到了对应的`class`文件，就不再往后继续搜索。如果所有路径下都没有找到，就报错。

## classpath的设定方法
- 在系统环境变量中设置`classpath`环境变量，**强烈**不推荐；
- 在启动JVM时设置`classpath`变量，推荐。

### Tips
在启动JVM时设置`classpath`才是推荐的做法。实际上就是给java命令传入`-classpath`或`-cp`参数：



## jar
如果有很多.class文件，散落在各层目录中，肯定不便于管理。如果能把目录打一个包，变成一个文件，就方便多了。

jar包就是用来干这个事的，它可以把package组织的目录层级，以及各个目录下的所有文件（包括.class文件和其他文件）都打成一个jar文件，这样一来，无论是备份，还是发给客户，就简单多了。

jar包实际上就是一个zip格式的压缩文件，而jar包相当于目录。如果我们要执行一个jar包的class，就可以把jar包放到classpath中：

```
java -cp ./hello.jar abc.xyz.Hello
```
这样JVM会自动在hello.jar文件里去搜索某个类。

### Tips
- 查看 .jar 源码的工具， [jd-gui.exe](http://java-decompiler.github.io/)
