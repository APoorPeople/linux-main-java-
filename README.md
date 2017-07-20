# linux-main-java-
Java项目在本地运行时，只需直接执行 run as java application程序就行，（main方法调用执行），
但是在服务器上我并没有现成的项目，想要在linux服务器上执行包含main方法的java文件，
可以将要执行的类文件打包为jar包，放到服务器上执行。具体方法：

# 一、将需要执行类文件编译后的class文件打包成jar包。例如：TestDemo.jar

# 二、使用WinRar方式打开jar包，找到META-INF文件夹下的的manifest.mf  ;
编辑该文件，文件格式必须如下：
Manifest-Version: 1.0
Main-Class: com.util.ParseURL------------//包名.类名
Class-Path: lib/commons-lang-2.5.jar lib/filterbuilder.jar lib/htmllexer.jar lib/htmlparser.jar lib/mysql-connector-java-5.1.7-bin.jar lib/poi-3.9-20121203.jar lib/sitecapturer.jar lib/thumbelina.jar
  
# 三、新建lib文件夹（为方便起见，最好将lib文件夹跟打包好的jar包放在同一目录下），
将类文件执行所需要的jar包放到lib文件夹下
注意：
          1、Class-Path为依赖的jar包的路径 。
           2、以上三项用英文冒号开始，冒号后要有一个空格。
           3、Class-Path中如果有很多项，写成一行打包的时候会报错line too long，这时需要把Class-Path分多行写。注意：从第二行开始，必须以两个空格开头

# 四、将现有文件及文件夹：TestDemo.jar文件 ， lib文件夹上传到linux服务器上的同一目录下， 这两个文件必须平级存放。跟Class-Path中的路径有关。

# 五：linux服务器上执行TestDemo.jar文件。
 java -jar TestDemo.jar 
将输出到控制台的结果打印到文件中
nohup java -jar TestDemo.jar   error.log
