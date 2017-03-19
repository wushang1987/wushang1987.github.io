

关于Java中使用的System对象，我们经常使用的是Systme.out.print ,而且也仅仅知道这是一个可以在控制台打印出语句，而没有去深究它的内在实现原理。下面我就详细地介绍System对象。 

1.JDK中有如下定义：.The System class contains several useful class fields and methods. It cannot be instantiated. 
也就是说System对象是不能被实例化的，只能通过调用它的属性和方法来使用它。 

2.System中的属性 Systme.in 是InputStream类型的，可以接受控制台输入的信息； System.out 和 System.err 都是PrintStream类型的 ，可以在控制台输出信息。 

3.System.getProperties() 返回的是Properties类型的对象，而返回的信息是Java虚拟机启动过程中所要加载的环境配置信息。可以通过下面的代码获取和输出信息，由于Properties是HashTable的一个子类，因此可以通过Map方法取出该集合中的元素 


Java代码 
[java] view plain copy
package javase.day18;    
    
import java.util.Properties;    
    
public class SystemDemo {    
    public static void main(String[] args) {    
        // TODO Auto-generated method stub    
        Properties prop=System.getProperties();    
        for(Object key:prop.keySet()){    
            String keyStr=(String)key;    
            String value=prop.getProperty(keyStr);    
            System.out.println(keyStr+" --- "+value);    
        }    
    }    
}    

结果：
控制台输出系统环境配置信息：

java.runtime.name --- Java(TM) SE Runtime Environment
sun.boot.library.path --- C:\Java\developerEnv\Java\jdk1.6.0_16\jre\bin
java.vm.version --- 14.2-b01
java.vm.vendor --- Sun Microsystems Inc.
java.vendor.url --- http://java.sun.com/
path.separator --- ;
java.vm.name --- Java HotSpot(TM) Client VM
file.encoding.pkg --- sun.io
sun.java.launcher --- SUN_STANDARD
user.country --- CN
sun.os.patch.level --- Service Pack 3
java.vm.specification.name --- Java Virtual Machine Specification
user.dir --- D:\workspace\BlackHorse
java.runtime.version --- 1.6.0_16-b01
java.awt.graphicsenv --- sun.awt.Win32GraphicsEnvironment
java.endorsed.dirs --- C:\Java\developerEnv\Java\jdk1.6.0_16\jre\lib\endorsed
os.arch --- x86
java.io.tmpdir --- C:\DOCUME~1\CHENGR~1\LOCALS~1\Temp\
line.separator --- 
......

......
......

使用以下代码也可以使控制台输出系统环境配置信息：

[java] view plain copy
public class SystemDemo {  
    public static void main(String[] args) {  
        System.getProperties().list(System.out);  
    }  
}  

4.可以通过System对象在系统中自定义一些特有的信息： 
System.setProperty(myKey , myValue); 


另外需要注意的一点是： 所谓的 system porperty，system 指的是 JRE (runtime)system，不是指 OS。 
System.setProperty("net.jxta.tls.principal", "client"); 
System.setProperty("net.jxta.tls.password", "password"); 
System.setProperty("JXTA_HOME",System.getProperty("JXTA_HOME","client")); 
可以利用系统属性来加载多个驱动


## 参考

http://blog.csdn.net/alex_zhuang/article/details/6918147

http://www.cnblogs.com/xuhuan/articles/1522212.html