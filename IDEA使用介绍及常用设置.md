# IDEA

IDEA面板

![image-20201122150543655](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122150543655.png)

1. 在Eclipse中我们有Workspace和Project的概念，在IDEA中只有Project和Module的概念。这里的对应关系为：

   | Eclipse中workspace相当于IDEA中的Project    |
   | ------------------------------------------ |
   | Eclipse中   Project   相当于IDEA中的Module |

   在IDEA中Project是最顶级的级别，次级别是Module。一个Project下可以有多个Module。
   
2. IDEA这样设置的原因：

   目前主流的大型项目都是分布式部署的，结构都是类似这种多Module的。

   这类项目一般都是这样划分的，比如：积分模块、任务模块、活动模块等等，模块之间彼此可以相互依赖。这些Module之间都是处于同一个项目业务下的模块，彼此之间是有不可分割的业务关系的。

   ```mermaid
   graph TD;
       项目-->模块1;
       项目-->模块2;
       项目-->模块3;
       项目-->模块4;
       项目-->模块5;
   ```

3. out目录的说明：里面存放的是编译后的字节码文件。

4. 删除模块：先Remove，后Delete。

## IDEA常用设置

1. 进入设置：

   ![image-20201122182913895](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122182913895.png)

   ![image-20201122182702066](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122182702066.png)

   ![image-20201122182845005](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122182845005.png)

2. 设置主题：

   ![image-20201122183017151](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122183017151.png)

3. 编辑区的字体变大或变小：

   ![image-20201122183146741](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122183146741.png)

4. 鼠标悬浮在代码上有提示：

   最新版的默认有提示。

5. 自动导包和优化多余的包：

   手动导包快捷键：Alt+enter(光标放在需要导包的代码)

   ![image-20201122184357942](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122184357942.png)

6. 同一个包下的类，超过指定个数的时候，导包合并为*

   ![image-20201122184722383](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122184722383.png)

   ![image-20201122185012833](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122185012833.png)

7. 显示行号， 方法和方法间的分隔符：

   ![image-20201122185348455](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122185348455.png)

8. 忽略大小写，进行提示：

   ![image-20201122185605194](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122185605194.png)

9. 多个类不隐藏，多行显示：

   ![image-20201122192520843](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122192520843.png)

10. 设置默认的字体，字体大小，字体行间距：

    ![image-20201122192704554](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122192704554.png)

11. 修改代码中注释的字体颜色：

    ![image-20201122193113480](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122193113480.png)

12. 修改类头的文档注释信息：-->注意：对新建的类才有效

    ```
    /**
    * @Author: wanghaoran
    * @Date: ${DATE} - ${MONTH} - ${DAY} - ${TIME}
    * @Description: ${PACKAGE_NAME}
    * @version: 1.0
    */
    ```

    ![image-20201122193645308](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122193645308.png)

13. 设置项目文件编码：

    ![](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122194046874.png)

    文件右下角可以调节编码格式：

    ![image-20201122194215801](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122194215801.png)

14. 自动编译：

    ![image-20201122194418330](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122194418330.png)

15. 省电模式：、

    ![image-20201122194636277](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122194636277.png)

16. 代码显示结构：

    ![image-20201122194806775](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122194806775.png)

17. 导入jar包：

    ![image-20201122194941351](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122194941351.png)

    ![image-20201122195028525](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122195028525.png)

    

18. 生成序列化版本号：

    ![image-20201122195344972](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122195344972.png)

    ![image-20201122195615562](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122195615562.png)

## IDEA常用快捷键

1. 创建内容：`alt+insert`

2. main方法：`psvm`

3. 输出语句：`sout`

4. 复制一行：`ctrl+d`(光标放在要复制的代码中，只能顺次复制)

5. 删除一行：`ctrl+y`

6. 代码向上/下移动：`ctrl+shift+up/down`

7. 搜索类：`ctrl+n`

8. 生成代码：`alt+insert`(如构造函数等)

9. 百能快捷键：`alt+enter`（导包，生成变量等）

10. 单行注释或多行注释：`ctrl+/`或`ctrl+shift+/`

11. 重命名：`shift+f6`

12. for循环：` fori`

13. 代码块包围：try-catch,if,while等 `ctrl+alt+t`

14. 代码自动补全：`alt+/`

    ![image-20201122204841302](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122204841302.png)

    ![image-20201122204940070](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122204940070.png)

15. idea代码字体大小放大和缩小的快捷键

    ![image-20201122205542683](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122205542683.png)

16. 代码一层一层调用的快捷键:

    点进源码：`ctrl+鼠标悬浮在代码上+点进去即可`

    back: `ctrl+shift+left`(页面打开才起作用)

    forward:`ctrl+shift+right`

17. 显示代码结构：`alt+7`

18. 显示导航栏：`alt+1`

19. 撤回：`ctrl+z`

20. REDO操作： `ctrl+shift+z`

    ![image-20201122202706438](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122202706438.png)

21. 缩进：`tab`  取消缩进: `shift+tab`

# 代码模板

所处位置：

1. Live Templates
2. Postfix Completion

![image-20201122212246564](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201122212246564.png)

区别：

1. Live Templates中可以做用户的个性化定制；Postfix Completion中只能用，不能修改。
2. 使用方式不同。

## 常用的代码模板

1. main方法

   `main`或者`psvm`

2. 输出语句

   `sout` 或者 `.sout`

   一些变型：

   `soutp`:打印方法的形参

   `soutm`:打印方法的名字

   `soutv`:打印变量

3. 循环

   普通for循环： `fori`(正向)  ` .fori`（正向）  ` .forr`(逆向)

   增强for循环：` iter ` 或者  `.for`

4. 条件判断

   `ifn`或者 `.null`:判断是否为null (if null)

   `inn` 或者 `.nn:` 判断不等于null(if not null)

5. 属性修饰符：

   `prsf`: private static final

   `psf`: public static final

## 修改代码模板

![ae92b3243ddba16937aa3944b47fc2fa](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/ae92b3243ddba16937aa3944b47fc2fa.png)

## 创建代码模板

![ccb61da579e51968f020497b0643314c](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/ccb61da579e51968f020497b0643314c-1606113077738.png)

# 断点调试

1. Debug的优化设置：更加节省内存空间：

   设置Debug连接方式，默认是Socket。Shared memory是Windows特有的一个属性，一般在Windows系统下建议使用此设置，内存占用相对较少。

   ![image-20201123091825406](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123091825406.png)

2. 常用断点

![image-20201123092912151](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123092912151.png)一步一步地向下运行代码，不会走入任何方法中。

![image-20201123093109879](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123093109879.png)一步一步地向下运行代码，不会走入系统类库的方法中，但是会进入自定义的方法中。

![image-20201123093124798](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123093124798.png)一步一步地向下运行代码，会走入系统类库的方法中，也会进入自定义的方法中。

![image-20201123093137622](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123093137622.png)跳出方法。

![image-20201123093148929](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123093148929.png)结束程序。

![image-20201123093201409](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123093201409.png)进入下一个断点，如果没有下一个断点，就直接运行到程序结束。

![image-20201123093245951](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123093245951.png)在当前次取消未执行的断点。

3. 条件判断

   ![image-20201123094405021](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123094405021.png)

   ![image-20201123094510485](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123094510485.png)直接在i=56时停下。

4. 查看表达是的值：

   选择行，`alt+f8`

# 创建JavaWeb项目（IDEA2020.2.3）

1. 创建项目不再是Java Enterprise了,而是先New 一个普通Java项目

   ![image-20201123112619588](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123112619588.png)

   ![image-20201123112705536](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123112705536.png)

2. 创建项目后,选择Run->Edit Configuration->左上角加号->Tomcat Server(注意不是TomEE)->Local

   ![image-20201123112814343](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123112814343.png)

   ![image-20201123112856651](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123112856651.png)

   ![image-20201123112929407](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123112929407.png)

   ![image-20201123113031900](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123113031900.png)

   ![image-20201123113114163](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123113114163.png)

   ![image-20201123113154534](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123113154534.png)

3. 回到项目界面,右键项目名称->add framwork support->选中Web Application->默认勾选创建web.xml

   ![image-20201123113328752](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123113328752.png)

   ![image-20201123113409543](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/image-20201123113409543.png)

4. 项目默认创建了一个index.jsp,你可以尝试启动看一下,右键run,启动需要时间

   ![step8](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/20200810144225812.png)

5. 页面访问成功,项目创建完成

   ![step9](IDEA%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D%E5%8F%8A%E5%B8%B8%E7%94%A8%E8%AE%BE%E7%BD%AE.assets/20200810144327823.png)

