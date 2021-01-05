# 第一章  基础及概念

## spring boot 2.x基础及概念入门

### 项目结构目录结构简介

![img](Spring%20Boot.assets/f2e8331e49ffdc5a35613d59c834ba88_460x429.png)
项目结构目录整体上符合maven规范要求：

| 目录位置                                  | 功能                                                         |
| :---------------------------------------- | :----------------------------------------------------------- |
| src/main/java                             | 项目java文件存放位置，初始化包含主程序入口 XxxApplication，可以通过直接运行该类来 启动 Spring Boot应用 |
| src/main/resources                        | 存放静态资源，图片、CSS、JavaScript、web页面模板文件等       |
| src/test                                  | 单元测试代码目录                                             |
| .gitignore                                | git版本管理排除文件                                          |
| target文件夹                              | 项目代码构建打包结果文件存放位置，不需要人为维护             |
| pom.xml                                   | maven项目配置文件                                            |
| application.properties（application.yml） | 用于存放程序的各种依赖模块的配置信息，比如服务端口，数据库连接配置等 |

- src/main/resources/static主要用来存放css、图片、js等开发用静态文件
- src/main/resources/public用来存放可以直接用于访问的html文件
- src/main/resources/templates用来存放web开发模板文件

## 需要先了解的核心概念

### 一、Spring Boot 、 Spring MVC 、Spring对比

首先你需要明白一件事情：Spring Boot项目目的并不是替换Spring、SpringMVC，而是使他们用起来更加简单。

**Spring 框架**

Spring框架最核心的特性就是依赖注入DI（Dependency Injecttion）和控制反转IOC（Inversion Of Control）。如果你能够合理的使用DI和IOC，可以开发出松耦合、扩展性好的的应用程序。

**Spring MVC**

Spring MVC提供了一种友好的方式来开发Web应用程序。 通过使用诸如Dispatcher Servlet，ModelAndView和View Resolver，可以轻松开发Web应用程序。

**Spring Boot**

Spring Boot期望通过结合自动配置和starters来解决大量的配置的问题。 另外，Spring Boot还提供了一些功能，可以更快地构建可用于生产环境的应用程序。

### 二、什么是Spring Boot Starter？

Spring Boot Starter是一组被依赖第三方类库的集合。

如果你要开发一个web应用程序，就通过包管理工具(如maven)引入spring-boot-starter-web就可以了，而不用分别引入下面这么多依赖类库，spring-boot-starter-web一次性帮你引入下面的这些常用类库。

- Spring — spring 核心, beans, context上下文, AOP面向切面
- Web MVC — Spring MVC
- Jackson — JSON数据的序列化与反序列化
- Validation — Hibernate参数校验及校验API
- 嵌入式 Servlet Container — Tomcat
- 日志框架Logging — logback, slf4j

### 三、什么是Spring Boot Starter Parent？

所有的Spring Boot项目默认使用spring-boot-starter-parent作为应用程序的父项目。继承父项目的好处在于： 统一java版本配置和其他的一些依赖类库的版本。

### 四、嵌入式web容器

Spring boot打成jar包，默认包含嵌入式的web容器：tomcat

## 如何使用lombok插件

1. 在IDEA中安装；
2. 在pom.xml里面加上如下依赖，插件生效。

```xml
 <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
</dependency>
```

### 使用lombok注解简化开发

#### 4.1 Data注解

在java类上使用@Data注解，将为我们在编译期自动生成

- 成员变量的get和set方法
- equals方法
- canEqual方法
- hashCode方法
- toString方法

#### 4.2 Slf4j注解

将在编译期自动帮我们引入Logger日志常量，我们在代码中就直接使用log.info或log.debug打印日志即可。下图中红色代码就用Slf4j注解代替就可以了。

#### 4.3 Builder注解

在Java类上使用Builder注解之后，我们可以使用如下代码为对象属性赋值。

#### 4.4 AllArgsConstructor注解

AllArgsConstructor注解将为我们在编译期自动生成：全参构造函数。有全参构造函数注解，自然就有无参构造函数注解：NoArgsConstructor注解。

##  devtools实现热加载

这是一种对于SpringBoot而言比较常见的一种实现方式。

### 1.1.引入devtools的maven依赖

```xml
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-devtools</artifactId>
   <optional>true</optional>
</dependency>
```

### 1.2.设置IDEA

- 首先，运行时编译配置：组合键：“Shift+Ctrl+Alt+/” ，选择 “Registry” ，选中打勾 “compiler.automake.allow.when.app.running” 。
  ![img](Spring%20Boot.assets/974e40a4165195960c5a4a888cbb78e3_1069x322.png)

## 开发过程中常用IDEA插件

### 一、Codota

极其强大的代码自动补全
![img](Spring%20Boot.assets/383d5c9d02cf0243f52071955d8d72b2_1146x540.gif)
当我们第一次使用某个类，对该类的某个函数不够熟悉时，可以通过该插件搜索相关用法，快速模仿学习。

### 二、Auto filling Java call arguments

开发中，我们通常会调用其他已经编写好的函数，调用后需要填充参数，但是绝大多数情况下，传入的变量名称和该函数的参数名一致，当参数较多时，手动单个填充参数非常浪费时间。
![img](Spring%20Boot.assets/5a88dbd7354eb90e77a7e7a134aa9d80_960x396.gif)
该插件就可以帮你解决这个问题。

安装完该插件以后，调用一个函数，使用 Alt+Enter 组合键，调出 "Auto fill call parameters" 自动使用该函数定义的参数名填充。

### 三、GsonFormat

GsonFormat插件工具可以快速的将JSON转换为实体类

```
{
    "id": 1,
    "author": "zimug",
    "title": "手摸手教你开发spring boot",
    "content": "c",
    "createTime": "",
    "reader":[{"name":"zimug","age":18},{"name":"kobe","age":37}]
}
```

插件安装好之后，先定义一个空的实体类（只有类名和花括号），使用快捷键Alt + S调出代码生成配置页面，相信后面你就都会了。这是根据JSON生成出来的对应的java bean的代码。

```java
public class Article {


    /**
     * id : 1
     * author : zimug
     * title : 手摸手教你开发spring boot
     * content : c
     * createTime :
     * reader : [{"name":"zimug","age":18},{"name":"kobe","age":37}]
     */

    private Long id;
    private String author;
    private String title;
    private String content;
    private String createTime;
    private List<ReaderBean> reader;



    public static class ReaderBean {
        /**
         * name : zimug
         * age : 18
         */

        private String name;
        private int age;

        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }

        public int getAge() {
            return age;
        }

        public void setAge(int age) {
            this.age = age;
        }
    }
}
```

### 四、Rainbow Brackets

代码由于括号太多，不确定当前代码行是否属于某个代码块，此时这个插件就会帮上大忙。
![img](Spring%20Boot.assets/1deb6c7746b514160057a7120a6b8054_937x190.png)

### 五、 Maven Helper

日常开发中，可能经常会遇到jar包冲突等问题，就需要通过查看maven依赖树来查看依赖情况。这种方式不是很高效，这里推荐一个插件，安装之后，直接打开pom文件，即可查看依赖数，还能自动分析是否存在jar包冲突。
![img](Spring%20Boot.assets/2ce747d125069867ff30894afb61d228_1384x885.png)

# 第二章 建立项目的过程

1. 在IDEA中新建项目，将application.properties改成application.yml，并配置端口号；

   ```xml
   server:
     port: 8888   # web应用服务端口
   ```

   ​	需不需要引入spring-boot-starter-web依赖，视情况而定：

	```xml
<dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-web</artifactId>
</dependency>
	```

2. 在pom.xml里面加上lombok依赖、配置热部署

	```xml
 <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
</dependency>
	```

	```xml
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-devtools</artifactId>
   <optional>true</optional>
</dependency>
	```

	首先，运行时编译配置：组合键：“Shift+Ctrl+Alt+/” ，选择 “Registry” ，选中打勾 “compiler.automake.allow.when.app.running” 。
	![img](Spring%20Boot.assets/974e40a4165195960c5a4a888cbb78e3_1069x322.png)
	
3. 在SpringBoot中集成MybatisPlus

   第一步：通过maven坐标将mybatis-plus-boot-starter以及数据库驱动引入到Spring Boot项目里面来。注意：引入`mybatis-plus-boot-starter`的项目就不需要引入`mybatis-spring-boot-starter`了

   ```xml
   <dependency>
       <groupId>com.baomidou</groupId>
       <artifactId>mybatis-plus-boot-starter</artifactId>
       <version>3.3.2</version>
   </dependency>
   <dependency>
       <groupId>mysql</groupId>
       <artifactId>mysql-connector-java</artifactId>
   </dependency>
   ```

   第二步：保证application.yml里面有数据库连接的配置。

   ```yaml
   spring:
     datasource:
       url: jdbc:mysql://192.168.161.3:3306/testdb?useUnicode=true&characterEncoding=utf-8&useSSL=false
       username: test
       password: 4rfv$RFV
       driver-class-name: com.mysql.cj.jdbc.Driver
   ```

   第三步：配置Mybatis的Mapper类文件的包扫描路径

   ```java
   @SpringBootApplication
   @MapperScan(basePackages = {"com.zimug.boot.launch.generator","com.zimug.boot.launch.mapper"})
   public class BootLaunchApplication {
   
       public static void main(String[] args) {
           SpringApplication.run(BootLaunchApplication.class, args);
       }
   
   }
   ```

4. 项目改成utf-8格式；
5. 从持久层写到控制层。

**注意**：当使用Mybatis Plus时，Mapper层应该这样写：

```java
public interface StudentMapper extends BaseMapper<Student> {
}
```

只写这个一句，记得在Application中加入@MapperScan注解。

# 第三章 Spring常用注解

## 一、HTTP协议的四种传参方式

| HTTP协议组成         | 协议内容示例                                     | 对应Spring注解 |
| :------------------- | :----------------------------------------------- | :------------- |
| path info传参        | /articles/12 (查询id为12的文章，12是参数)        | @PathVariable  |
| URL Query String传参 | /articles?id=12                                  | @RequestParam  |
| Body 传参            | Content-Type: multipart/form-data                | @RequestParam  |
| Body 传参            | Content-Type: application/json，或其他自定义格式 | @RequestBody   |
| Headers 传参         |                                                  | @RequestHeader |

## 二、常用注解

### 1.  @RequestBody与@ResponseBody

```java
//注意并不要求@RequestBody与@ResponseBody成对使用。
public @ResponseBody  AjaxResponse saveArticle(@RequestBody ArticleVO article)
```

- @RequestBody修饰请求参数，用于**接收**HTTP的body，默认是使用JSON的格式
- @ResponseBody修饰返回值，用于**返回**HTTP的body，默认是使用JSON的格式。

### 2. @RequestMapping 注解方法

```java
@RequestMapping(value = "/article", method = POST)
@PostMapping(value = "/article")
```

上面代码中两种写法起到的是一样的效果。

### 3. @RestController与@Controller 注解类

@Controller表明一是Controller层，二是使@RequestMapping起作用；

@RestController相当于 @Controller和@ResponseBody结合。

### 4. @PathVariable 与@RequestParam  注解参数

PathVariable用于URI上的{参数}，通常比较小。

```java
@GetMapping("/articles/{id}")
    public AjaxResponse  getArticle(@PathVariable("id") Long id)
```

### 5. @Service、@Repository 与@compent 注解类

@Service表明是Service层，@Repository 表明是持久层不知道是什么层用@compent

### 6. @Resource与@Autowired 注解对象

两者的功能都是new一个新对象，但是通常使用@Resource

### 7. @Mapper与@MapperScan

1. @Mapper注解：
   作用：在接口类上添加了@Mapper，在编译之后会生成相应的接口实现类
   添加位置：接口类上面

   ```java
   @Mapper
   public interface UserDAO {
      //代码
   }
   ```

   如果想要每个接口都要变成实现类，那么需要在每个接口类上加上@Mapper注解，比较麻烦，解决这个问题用@MapperScan.

2. @MapperScan
   作用：指定要变成实现类的接口所在的包，然后包下面的所有接口在编译之后都会生成相应的实现类
   添加位置：是在Springboot启动类上面添加

   ```java
   @SpringBootApplication
   @MapperScan("com.winter.dao")
   public class SpringbootMybatisDemoApplication {
   
       public static void main(String[] args) {
           SpringApplication.run(SpringbootMybatisDemoApplication.class, args);
       }
   }
   ```

3. 使用@MapperScan注解多个包

   ```java
   @SpringBootApplication  
   @MapperScan({"com.kfit.demo","com.kfit.user"})  
   public class App {  
       public static void main(String[] args) {  
          SpringApplication.run(App.class, args);  
       }  
   } 
   ```

### 8. @Transactional 事务

service层中有事务，要在方法上加上@Transactional注解

# 第四章 spring boot 配置管理

## profile不同环境使用不同配置

### 一、配置文件规划

我们开发的服务通常会部署在不同的环境中，例如开发环境、测试环境，生产环境等，而不同环境需要不同的配置。最典型的场景就是在不同的环境下需要连接不同的数据库，需要使用不同的数据库配置。

全局配置文件:application.yml
开发环境配置文件：application-dev.yml
测试环境配置文件：application-test.yml
生产环境配置文件：application-prod.yml

## 二、切换环境的方式

### 1. 通过配置application.yml

application.yml是默认使用的配置文件，在其中通过spring.profiles.active设置使用哪一个配置文件，下面代码表示使用application-prod.yml配置，如果application-prod.yml和application.yml配置了相同的配置，比如都配置了运行端口，那application-prod.yml的优先级更高

```yaml
#需要使用的配置文件
spring:
  profiles:
    active: prod
```

Mybatis中模糊查询：

```sql
s.name like concat('%',#{name},'%')
```

