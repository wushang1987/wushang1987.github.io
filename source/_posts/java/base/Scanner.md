---
title: java scanner
date: 2017-04-16 11:29:00
tags:
    - java
---

java.util.Scanner是Java5的新特征，主要功能是简化文本扫描。这个类最实用的地方表现在获取控制台输入，其他的功能都很鸡肋，尽管Java API文档中列举了大量的API方法，但是都不怎么地


一、扫描控制台输入

这个例子是常常会用到，但是如果没有Scanner，你写写就知道多难受了。
当通过new Scanner(System.in)创建一个Scanner，控制台会一直等待输入，直到敲回车键结束，把所输入的内容传给Scanner，作为扫描对象。如果要获取输入的内容，则只需要调用Scanner的nextLine()方法即可。

/** 
* 扫描控制台输入 
* 
* @author leizhimin 2009-7-24 11:24:47 
*/ 
public class TestScanner { 
        public static void main(String[] args) { 
                Scanner s = new Scanner(System.in); 
                System.out.println("请输入字符串："); 
                while (true) { 
                        String line = s.nextLine(); 
                        if (line.equals("exit")) break; 
                        System.out.println(">>>" + line); 
                } 
        } 
}


请输入字符串： 
234 
>>>234 
wer 
>>>wer 
bye 
>>>bye 
exit 

Process finished with exit code 0

先写这里吧，有空再继续完善。

二、如果说Scanner使用简便，不如说Scanner的构造器支持多种方式，构建Scanner的对象很方便。

可以从字符串（Readable）、输入流、文件等等来直接构建Scanner对象，有了Scanner了，就可以逐段（根据正则分隔式）来扫描整个文本，并对扫描后的结果做想要的处理。

三、Scanner默认使用空格作为分割符来分隔文本，但允许你指定新的分隔符

使用默认的空格分隔符：
        public static void main(String[] args) throws FileNotFoundException { 
                Scanner s = new Scanner("123 asdf sd 45 789 sdf asdfl,sdf.sdfl,asdf    ......asdfkl    las"); 
//                s.useDelimiter(" |,|\\."); 
                while (s.hasNext()) { 
                        System.out.println(s.next()); 
                } 
        }


123 
asdf 
sd 
45 
789 
sdf 
asdfl,sdf.sdfl,asdf 
......asdfkl 
las 

Process finished with exit code 0


将注释行去掉，使用空格或逗号或点号作为分隔符，输出结果如下：
123 
asdf 
sd 
45 
789 
sdf 
asdfl 
sdf 
sdfl 
asdf 







asdfkl 

las 

Process finished with exit code 0



四、一大堆API函数，实用的没几个

（很多API，注释很让人迷惑，几乎毫无用处，这个类就这样被糟蹋了，启了很不错的名字，实际上做的全是龌龊事）

下面这几个相对实用：

delimiter() 
          返回此 Scanner 当前正在用于匹配分隔符的 Pattern。
hasNext() 
          判断扫描器中当前扫描位置后是否还存在下一段。（原APIDoc的注释很扯淡）
hasNextLine() 
          如果在此扫描器的输入中存在另一行，则返回 true。
next() 
          查找并返回来自此扫描器的下一个完整标记。
nextLine() 
          此扫描器执行当前行，并返回跳过的输入信息。


五、逐行扫描文件，并逐行输出

看不到价值的扫描过程
        public static void main(String[] args) throws FileNotFoundException { 
                InputStream in = new FileInputStream(new File("C:\\AutoSubmit.java")); 
                Scanner s = new Scanner(in); 
                while(s.hasNextLine()){ 
                        System.out.println(s.nextLine()); 
                } 
        }


package own; 

import java.io.BufferedReader; 
import java.io.BufferedWriter; 
import java.io.InputStream; 
import java.io.InputStreamReader; 
import java.io.OutputStreamWriter; 
import java.net.HttpURLConnection; 
import java.net.ProtocolException; 
import java.net.URL; 

import com.verisign.uuid.UUID; 

/** 
* @author wangpeng 
* 
*/ 
public class AutoSubmit { 

  /** 
    * @param args 
    * @throws Exception    
    */ 
  public static void main(String[] args) throws Exception { 

...在此省略N行 

Process finished with exit code 0


Java对字符串支持还是比较弱的，尽管Java一直在努力。

## 参考文献


http://bbs.itheima.com/thread-90856-1-1.html