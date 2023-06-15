# 第一个Java程序：Hello World！

### **Hello World 程序**

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("hello world");
    }
}
```

**使用cmd运行程序**

[![pCu9y0e.png](https://s1.ax1x.com/2023/06/14/pCu9y0e.png)](https://imgse.com/i/pCu9y0e)

**Java程序运行的流程**

[![pCuJZxP.jpg](https://s1.ax1x.com/2023/06/15/pCuJZxP.jpg)](https://imgse.com/i/pCuJZxP)

**注意事项：**

1. Java文件名与public class的名称一致
2. 1个Java文件可以包含多个class，但只能有一个public class
3. main方法是Java程序的入口方法[固定格式]
4. Java代码每行的结束需要使用分号，代码块需要使用大括号包裹起来

### 注释

```java
   /**
     * 文档注释
     * @param age   年龄
     * @param name  姓名
     * @return  
     */
    String testExplanatory(Integer age,String name){
//        String s=null;    单行注释
        
//        多行注释
        /*for (int i = 0; i < 100; i++) {
            System.out.println(i );
        }*/
        return null;
    }
```

### 补充知识

1. JDK12 安装时需要自己配置JRE，JDK1.5以后在环境变量中不用配置classpath
2. 反编译工具：将class、jar 反编译成java文件的工具，例如jd-gui
