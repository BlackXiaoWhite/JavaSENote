# Java流程控制语句

**Java流程控制分为顺序结构、分支结构、循环结构**

**顺序结构**：从上到下依次顺序执行，这里不赘叙了

### 分支结构

#### if语句

**分支结构又称为选择结构，分为单分支、双分支、多分支、嵌套分支，频繁使用多个单分支效率极低**

**案例一**：会员登录，如果用户名是 ‘青’，并且密码 123,输入欢迎您青，否则输出，对不起，您不是会员

```java
    public static void main(String[] args) {
        /**
         * if双分支案例
         */
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入用户名");
        String userName = scanner.next();
        System.out.println("请输入密码");
        String passWord = scanner.next();
        if ("青".equals(userName)&&"123456".equals(passWord)){
            System.out.println("欢迎您！青");
        }else{
            System.out.println("对不起，您不是会员");
        }
    }
```

**案例二**：会员购物时，根据积分的不同享受不同的折扣

| 会员积分X    | 折扣 |
| ------------ | ---- |
| x<2000       | 9折  |
| 2000<=x<4000 | 8折  |
| 4000<=x<8000 | 7折  |
| x>=8000      | 6折  |

```java
   public void memberShopping(Integer integral){
        /**
         * if多分支案例
         */
        if(integral>=8000){
            System.out.println("可享受6折");
        }else if(integral>=4000){
            System.out.println("可享受7折");
        }else if(integral>=2000){
            System.out.println("可享受8折");
        }else{
            System.out.println("可享受9折");
        }
    }
```



**案例三**：普通顾客购物满100元打9折；会员购物打8折；会员购物满200元打7.5折

```java
    /**
     * 计算用户消费的金额
     * @param moneyj    金额
     * @param state     状态 1-普通用户 2-会员
     */
    public void customerShopping(Integer money,Integer state){
        if (state==1){
            if (money>=100){
                System.out.printf("普通消费者，消费%f",money*0.9);
            }
        }else {
            if (money>=200){
                System.out.printf("会员，消费%f",money*0.75);
            }else if(money>=100){
                System.out.printf("会员，消费%f",money*0.8);
            }
        }
    }
```



#### switch语句

switch语句是多分支选择语句，它**只能进行等值判断**，表达式必须为**byte、short、int、char、String**类型，default子句是可选子句，如果上面的case条件均不满足，则执行default子句

> **switch语句：每个case模块一定要添加break**
>
> **switch与if的区别：**
>
> switch只能进行等值判断；if没有限制，适合判断处于某个区间的情况

**案例**：根据月份判断季节

```java
 /**
     * 根据月份 判断季节
     * @param month
     */
    public void season(Integer month){
        switch (month){
            case 3: case 4: case 5:
                System.out.println("春季");
                break;
            case 6: case 7: case 8:
                System.out.println("夏季");
                break;
            case 9: case 10: case 11:
                System.out.println("秋季");
                break;
            case 12: case 1: case 2:
                System.out.println("冬季");
                break;
            default:
                System.out.println("入参错误");
        }
    }
```

### 循环结构

循环结构分为**while、do while、for三种**，**循环的四要素**是**初始化、条件判断、循环体、迭代条件**

**while语句**：先判断、再执行

```java
    /**
     * while 语句案例：输出0-100
     *      初始化语句：int num=0;
     *      条件判断语句：num<=100
     *      循环体： System.out.println(num++);
     *      迭代条件：num++
     */
    public void whileTest(){
       int num=0;
       while (num<=100){
           System.out.println(num++);
       }
    }
```

**do while语句**：先执行，再判断

```java
    /**
     * do while语句案例：
     *      判断条件是num<100,但是do while语句是先执行 后判断，所以程序会执行一次循环体
     */
    public void doWhileTest(){ 
        int num=101;
        do{
            System.out.println(num++);
        }while (num<100);
    }
```

**for语句**：相比while语句，书写起来更加简洁方便

```java
    /**
     * for语句案例：
     *      for(初始化语句;条件判断语句;步进[迭代条件语句]){
     *          循环体
     *      }
     */
    public void forTest() {
        for (int i = 0; i <= 100; i++) {
            System.out.println(i);
        }
    }
```

>**for语句与while的区别**：
>
>初始化的变量作用域不同，for语句：变量的作用域是for结构内；while语句：变量的作用域是方法内
>
>**建议**：
>
>​	for语句：适合已知明确循环次数时使用
>
>​	while语句：适合明确判断条件，但不明确循环次数时使用

**案例：**

[![pCMGhvt.jpg](https://s1.ax1x.com/2023/06/16/pCMGhvt.jpg)](https://imgse.com/i/pCMGhvt)

```java
    /**
     * 思路：
     * 1、购买商品时：使用while，当不需要购买时 break
     * 2、支付金额时：使用while，当支付成功时break
     * 3、商品信息打印简单的使用了switch实现，单价也是常量，商品如果是一个对象的话，效果会更好，作者比较偷懒~
     * @param args
     */
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("******************************\n请选择以下商品:\n1-羽毛球\t2-篮球\t3-足球\n******************************");
        int sum=0;
        while(true){
            System.out.print("\n请输入商品编号：");
            int id = scanner.nextInt();
            System.out.print("请输入商品数量：");
            int num = scanner.nextInt();
            switch (id){
                case 1:
                    System.out.printf("羽毛球 ￥69 数量：%d 合计：%d\n",num,num*69);
                    sum+=num*69;
                    break;
                case 2:
                    System.out.printf("篮球 ￥100 数量：%d 合计：%d\n",num,num*100);
                    sum+=num*100;
                    break;
                case 3:
                    System.out.printf("足球 ￥140 数量：%d 合计：%d\n",num,num*140);
                    sum+=num*140;
                    break;
                default:
                    System.out.println("编号输入错误");
            }
            System.out.print("是否继续（y/n）");
            String next = scanner.next();
            if ("n".equals(next))
                break;
        }
        System.out.printf("应付金额：%d",sum);
        while(true){
            System.out.print("\n实付金额：");
            int money = scanner.nextInt();
            if (money<sum){
                System.out.println("实付金额少于应付金额,重新支付");
            }else{
                System.out.printf("找钱：%d",money-sum);
                break;
            }
        }
    }
```

**案例：十进制转成二进制输出**

```java
   /**
     * 案例：十进制转换二进制
     * 思路：
     *      在循环中：将取到的模进行拼接，反复将得到的商赋给变量 直到商为0时 break
     */
    public String convert(int number) {
        String byteStr="";
       while (number!=0){
           byteStr+=number%2;
           number/=2;
       }
       byteStr=new StringBuffer(byteStr).reverse().toString();
       return byteStr;
    }

```

**案例：乘法表**

```java
    /**
     * 乘法表案例 循环嵌套的经典案例
     */
    public void multiplication(){
        for (int i = 1; i <10 ; i++) {
            for (int j = 1; j <=i ; j++) {
                System.out.printf("%dx%d=%d\t",i,j,i*j);
            }
            System.out.println();
        }
    }
```
### 递归算法（递归结构）

**程序调用自身的编程技巧**称为**递归**，递归的特点：

- 一个问题可被分解为若干层简单的子问题
- 子问题和其上层问题的解决方案一致
- 外层问题的解决依赖于子问题的解决

递归结构分为两个部分：**递归结束条件、递归体**

**案例：斐波那契数列**

```java
    /**
     * 递归案例：斐波那契数列（1，1，2，3....）
     * 规律：除了前两位是1 其余都是前两位的和
     */
    public void recursionTest(){
        for (int i = 1; i <=10; i++) {
            System.out.printf("%d \t",recursion(i));
        }
    }

    /**
     *  递归方法：获取第n个元素的值
     */
    public Integer recursion(Integer number){
        if (number==1||number==2){
            return 1;
        }else{
            return recursion(number-1)+recursion(number-2);
        }
    }
```
### 补充知识

#### Scanner

**Scanner是文件扫描器，System.in是标准输入流，设计模式是装饰者模式**

#### 跳出语句

跳出语句有**break、continue、return**

**break**：可以用于switch和循环结构中（跳出整个循环）

**continue**：只能在循环结构中使用（跳出单次循环）

**return**：返回方法的返回值、终止当前方法

​	**终止方法运行的方式还有：System.exit(100);**
