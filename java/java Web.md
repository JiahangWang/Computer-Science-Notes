# <center>java WEB</center>

## <font class="text-color-13" color="#ffeb3b">B/S 架构的系统通信原理</font>
- web 系统的访问过程
	1. 打开浏览器
	2. 找到地址栏
	3. 输入一个合法的网址
	4. 回车
	5. 在浏览器上显示响应的结果
	
- 关于网址：
	- 网址（URL 统一资源定位符）如：https://www.baidu.com/
	- www.baidu.com 是一个域名
	- 在浏览器地址栏上输入域名，回车之后域名解析器会将域名解析出来一个具体的IP地址和端口号等
	- 解析结果如：http://104.193.88.123/index.html  `http://IP地址:端口号/资源路径`

- IP 地址
	- 计算机在网络当中的一个身份证号码。在同一个网络当中，IP 地址是唯一的
	- A 计算机想要和 B 计算机通信，需要先知道 B 计算机的 IP 地址，有了 IP 地址才能建立连接

- 端口号
	- 一个端口代表一个软件（一个端口代表一个软件，一个端口仅代表一个服务）
	- 一个计算机当中有很多软件，每一个软件启动之后都有一个端口号
	- 在同一个计算机上，端口号具有唯一性

- web 系统通信原理
	1. 用户输入网址（URL），如：https://www.baidu.com/
	2. 域名解析器进行域名解析，如：http://104.193.88.123/index.html
	3. 浏览器软件在网络中搜索 `104.193.88.123` 这台主机上的服务器软件，因为是 `80` 端口，所有可以定位到 80 端口对应的软件
	4. `80` 端口对应的服务器软件查找资源路径对应的 `html` 文件
	5. 服务器将 `html` 文件中的内容直接输出响应到浏览器上
	6. 浏览器接收到来自服务器的代码（html css javascript）
	7. 浏览器渲染，执行 html css javascript 代码，展示网页效果

示例：

![](https://huatu.98youxi.com/markdown/work/uploads/upload_b17280141509f18bbc4bc2993f206518.png)

## <font class="text-color-13" color="#ffeb3b">服务器</font>
- 分为 web 服务器和应用服务器

- Web服务器主要负责接收和响应HTTP请求，处理静态资源（如HTML、CSS、JavaScript文件等）并将请求转发到应用服务器。Web服务器通常具有高性能、高可用性和可扩展性的特点，可以处理大量的并发请求。

- 应用服务器主要负责执行应用程序的业务逻辑，通常运行在Web服务器的后台，与Web服务器通过某种通信协议进行交互。应用服务器提供了一系列的服务和功能，如连接池、事务管理、JNDI、远程调用等，可以帮助应用程序更高效地运行。

- 应用服务器实现了 javaEE 的所有规范。web 服务器只实现了 javaEE 中的 Servlet + JSP 两个核心的规范

### <font class="text-color-15" color="#ff9800">常用的Web服务器软件</font>
1. Apache HTTP Server：是最常用的Web服务器之一，可在各种操作系统上运行。
  
2. Nginx：是一个高性能的Web服务器，也被广泛用作反向代理和负载均衡器。
  
3. Microsoft IIS：是运行在Windows操作系统上的Web服务器软件，通常与ASP.NET框架一起使用。
  
4. Lighttpd：是另一种轻量级的Web服务器，被设计为快速、安全、灵活和可扩展的。
  
5. Caddy：是一个现代化的Web服务器，提供自动化的TLS证书管理和易于使用的配置。
  
6. Tomcat：是一个流行的Java Servlet容器和Web服务器，被广泛用于Java Web应用程序的开发和部署。

### <font class="text-color-15" color="#ff9800">常用的应用服务器软件</font>
1. Apache Tomcat：是一个流行的Java Servlet容器和Web服务器，可用于Java Web应用程序的开发和部署。
  
2. JBoss：是一个开源的Java应用服务器，提供高度可定制的Java EE平台，包括EJB、JPA、JMS等。
  
3. WebLogic：是Oracle开发的一个Java EE应用服务器，提供了一系列Java EE的实现，包括EJB、JMS、JPA等。
  
4. WebSphere：是IBM开发的一个Java EE应用服务器，提供高度可定制的Java EE平台，包括EJB、JMS、JPA等。
  
5. GlassFish：是一个开源的Java EE应用服务器，实现了Java EE 7规范，包括EJB、JMS、JPA等。

## <font class="text-color-13" color="#ffeb3b">Tomcat</font>
- [Tomcat下载地址](https://tomcat.apache.org/download-10.cgi)
### <font class="text-color-15" color="#ff9800">Tomcat 服务器软件重要目录</font>
1. bin：包含了 Tomcat 的可执行文件，例如启动和停止 Tomcat 的脚本文件。
  
2. conf：包含了 Tomcat 的配置文件，包括服务器配置和应用程序配置等。其中的 server.xml 文件是最重要的配置文件（可以在里面配置端口号，默认 Tomcat 端口是 `8080`），它定义了 Tomcat 服务器的全局配置信息。
  
3. lib：包含了 Tomcat 的 Java 类库和其他库文件，例如 JDBC 驱动程序。
  
4. logs：包含了 Tomcat 的日志文件，例如访问日志和错误日志等。
  
5. webapps：这是 Tomcat 中部署 Web 应用程序的目录。将 WAR 文件放到这个目录中，Tomcat 就会将其解压并部署在服务器上。
  
6. work：这个目录包含了 Tomcat 运行时生成的文件，例如编译 JSP 页面时生成的类文件等。

### <font class="text-color-15" color="#ff9800">环境变量</font>
* 在配置 Tomcat 服务器之前，需要确保已经正确设置了以下环境变量：

1. JAVA_HOME：这个环境变量指向你的 Java 安装目录。Tomcat 服务器是由 Java 编写并运行的，因此需要确保已经正确安装了 Java 并设置了 JAVA_HOME 环境变量。
  
2. CATALINA_HOME：这个环境变量指向你的 Tomcat 安装目录。在配置 Tomcat 服务器之前，你需要先下载和安装 Tomcat，并设置 CATALINA_HOME 环境变量，以便系统知道 Tomcat 的安装位置。
  
3. PATH：这个环境变量包含了系统查找可执行程序的路径。你需要将 Tomcat 的 bin 目录添加到 PATH 环境变量中，以便能够在终端或命令行中直接运行 Tomcat 的脚本文件，比如 `startup.sh` 和 `shutdown.sh`。（windows 是 `.bat` 结尾）(可以重命名这两个命令)

### <font class="text-color-15" color="#ff9800">启动/关闭 Tomcat 服务器</font>
- 在终端执行对应操作系统的脚本文件（这里 windows 为例）
- 启动：`startup.bat`
- 关闭：`shutdown.bat`
#### <font class="text-color-7" color="#03a9f4">测试 Tomcat 服务器是否启动成功</font>
- 访问默认网站：启动 Tomcat 后，可以在 Web 浏览器中输入 `http://localhost:8080` 或者 `http://127.0.0.1:8080`，这是 Tomcat 默认的网站地址。如果 Tomcat 服务器已经成功启动，你将能够看到 Tomcat 的默认欢迎页面。如果无法访问该页面，则可能是服务器未能成功启动或端口被占用。

#### <font class="text-color-7" color="#03a9f4">解决 Tomcat 服务器在启动时控制台的乱码问题</font>
* 把 Tomcat 根目录下 conf 文件夹下面的 logging.properties 文件中的 `java.util.logging.ConsoleHandler.encoding` 属性改为 `GBK`

## <font class="text-color-13" color="#ffeb3b">B/S 结构系统的角色和协议</font>
### <font class="text-color-15" color="#ff9800">角色：</font>

![](https://huatu.98youxi.com/markdown/work/uploads/upload_a38791622884745c385fccab5e0d61fc.png)

1. 浏览器软件 (例如 Google Chrome, Safari, Firefox)
2. WEB Server (例如 Apache, Nginx, IIS)
3. DB Server (例如 MySQL, Oracle, MongoDB)
4. Webapp (例如 淘宝网, 新浪微博, 豆瓣读书)

### <font class="text-color-141" color="#ff9800">协议：</font>

![](https://huatu.98youxi.com/markdown/work/uploads/upload_26af6cc9192708818423a75f23f39d1e.png)

1. 浏览器与 WEB Server 之间遵守 HTTP 协议，通过 HTTP 请求和响应来进行通信。
2. WEB Server 与 DB Server 之间遵守一种或多种数据库通信协议（如MySQL 的TCP协议或Oracle的TNS协议），以便 WEB Server 可以读写数据库。
3. Webapp 的前端与浏览器之间通常采用 HTML、CSS、JavaScript等 Web 标准技术来进行交互和渲染页面，后端与 WEB Server 之间则通常采用一种或多种服务器端编程语言（如 PHP、Python、Java 等）和框架（如 Flask、Django 等）来处理请求和响应。

## <font class="text-color-13" color="#ffeb3b">Servlet</font>
* Servlet是Java Web应用程序中的一种Java类，用于处理Web请求和响应。Servlet可以看作是Web服务器和Web应用程序之间的中间层，它们能够接收来自Web浏览器的HTTP请求并生成HTTP响应。Servlet通常用于创建动态Web页面，并且可以执行与数据库和其他应用程序集成相关的任务。Servlet可以处理各种HTTP请求，包括GET、POST和PUT等请求方法。Servlet通常使用Java Servlet API编写，并在Java Servlet容器（如Apache Tomcat或JBoss）中部署和运行。通过使用Servlet技术，Web开发人员可以构建高性能和可扩展的Web应用程序。

### <font class="text-color-141" color="#ff9800">模拟 Servlet 本质</font>
* Servlet 接口（SUN 指定）
```java
public interface Servlet {
    void service();
}
```
- Servlet 实现类（Webapp 开发人员编写）
```java
public class UserLoginServlet implements Servlet{
    @Override
    public void service() {
        System.out.printf("UserLogin 服务开始...\n");
    }
}
```
```java
public class AccountTransferServlet implements Servlet{
    @Override
    public void service() {
        System.out.printf("AccountTransfer 服务开始...\n");
    }
}
```
- 解析配置文件（Webapp 开发人员编写）
```
/aaa=UserLoginServlet  
/bbb=AccountTransferServlet
```
- Tomcat 服务器调用方法（服务器开发人员编写）
```java
public class Tomcat {
    public static void main(String[] args) throws ClassNotFoundException, InstantiationException, IllegalAccessException {

        // 模拟接受访问路径
        Scanner scanner = new Scanner(System.in);
        System.out.printf("Tomcat服务器启动成功，开始接收用户访问：");
        String key = scanner.nextLine();

        // 通过 key 获取 value
        ResourceBundle bundle = ResourceBundle.getBundle("pathToServlet");
        String servletClassName = bundle.getString(key);

        // 通过反射机制创建对象
        Class clazz = Class.forName(servletClassName);
        Servlet servlet = (Servlet) clazz.newInstance();

        // 调用 Servlet 对象中的方法
        servlet.service();
    }
```
### <font class="text-color-141" color="#ff9800">注意</font>
- 解析配置文件有固定的文件名，文件路径，都是 SUN 制定的 Servlet 规范中的明细

- Servlet 规范中规定了
	- webapp 的目录结构
	- webapp 解析配置文件的文件名、路径、内容
	- webapp 中 java 程序存放的位置

- Tomcat 等服务器要遵循 Servlet 规范。javaWeb程序员也需要遵守 Servlet 规范。这样 Tomcat 等服务器和 webapp 才能够解耦合

## <font class="text-color-13" color="#ffeb3b">开发带有 Servlet 的 webapp 步骤</font>
- 第一步：在 webapps 目录下新建一个目录，起名 `crm` （这个 crm 就是 webapp 的名字）。也可以是其他项目，如银行项目可以创建一个目录 bank，办公系统可以创建一个目录 oa 
	- 注：crm 就是这个 webapp 的根

- 第二步：在 webapp 的根下新建一个目录： `WEB-INF` 

- 第三步：在 WEB-INF 目录下新建一个目录：`classes`
	- 注：这个目录下存放的一定是 java 程序编译之后的 class 文件（这里存放的是字节码文件）

- 第四步：在 WEB-INF 目录下新建一个目录：`lib`
	- 注：这个目录不是必须的，但是一个 webapp 如果需要第三方 jar 包的话，jar 包需要放到这个 lib 目录下

- 第五步：在 WEB-INF 目录下新建一个文件：`web.xml `
	- 注：这个 web.xml 文件就是一个配置文件，描述了请求路径和 Servlet 类之间的关系对照表。
	- 例如：
```xml
<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns="https://jakarta.ee/xml/ns/jakartaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://jakarta.ee/xml/ns/jakartaee
                      https://jakarta.ee/xml/ns/jakartaee/web-app_6_0.xsd"
  version="6.0"
  metadata-complete="true">

</web-app>
```
- 第六步：编写 java 程序，这个 java 小程序也不能随意开发，必须实现 Servlet 接口。
	- 这个 Servlet 接口不在 JDK 当中。属于 javaEE，是另一套类库
	- 
	- Tomcat 服务器实现了 Servlet 规范，所以 Tomcat 服务器也需要使用 Servlet 接口。（Tomcat 服务器的 CATALINA_HOME\lib 目录下有一个 servlet-api.jar，解压后里面有一个 `Servlet.class` 文件）
		- 注：javaEE 8 或之前对应的 Servlet 类名是：`javax.servlet.Servlet`，JakartaEE 9 时对应的 Servlet 类名是：`Jakarta.servlet.Servlet`
		- [JakartaEE 9 文档](https://jakarta.ee/specifications/platform/9/apidocs/)

- 第七步：编译我们编写的 java 文件（实现了 Servlet 接口）
	- 注：编译时需要 servlet-api.jar 文件一起编译，可以选择配置环境变量，`CLASSPATH = 文件路径`
	- 编译后的 `Class` 文件放在 `classes` 目录下即可

- 第八步：在 `web.xml` 文件中注册实现的 Servlet 类
```xml
<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns="https://jakarta.ee/xml/ns/jakartaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="https://jakarta.ee/xml/ns/jakartaee"
         xsi:schemaLocation="https://jakarta.ee/xml/ns/jakartaee
                      https://jakarta.ee/xml/ns/jakartaee/web-app_6_0.xsd"
         version="6.0"
         metadata-complete="true">

        <!--servlet 描述信息-->
        <servlet>
            <!--名字-->
            <servlet-name>abc</servlet-name> 
            <!--这个位置必须是带有包名的全限定类名-->
            <servlet-class>UserLoginServlet</servlet-class>
        </servlet>

        <!--servlet 映射信息-->
        <servlet-mapping>
            <!--这里名字需要和上面一样-->
            <servlet-name>abc</servlet-name>    
            <!--这里需要一个路径，以 "/" 开始-->
            <url-pattern>/abc/def</url-pattern>
        </servlet-mapping>
</web-app>
```

- 第九步：启动 Tomcat 服务器

- 第十步：打开浏览器，在浏览器当中输入一个 URL，这个 URL 为：
	- http://127.0.0.1:9090/crm/abc/def
	- 注：浏览器上的请求路径不能随便写，这个请求路径必须和 `web.xml` 文件中的 `url-pattern` 一致
	- 浏览器上的请求路径和 `web.xml` 文件中的 `url-pattern` 唯一区别就是，浏览器上的带有项目名：`crm`

#### <font class="text-color-7" color="#03a9f4">流程</font>
- 浏览器发送请求，到最终服务器调用 Servlet 中的方法，大致流程：
	- 用户输入 URL 或点击超链接：`http://127.0.0.1:9090/crm/abc/def`

	- Tomcat 服务器收到请求，截取路径：`crm/abc/def`
	- Tomcat 服务器找到项目
	- Tomcat 服务器在项目文件夹中的 `web.xml` 文件中找到 `/abc/def` 对应的 Servlet 是 `UserLoginServlet`
	- Tomcat 服务器通过反射机制，创建 `UserLoginServlet` 的对象，并调用对象的 `service` 方法


### <font class="text-color-141" color="#ff9800">注意</font>
* 浏览器上编写 `url-pattern` 的路径太复杂，需要在 `WEB-INFO` 文件夹之外编写一个文件 `index.html` ，通过在里面放入这个路径的超链接来实现开启服务

### <font class="text-color-141" color="#ff9800">标准 web 应用程序目录结构</font>
- `WEB-INF`目录：包含Web应用程序的配置和资源文件。

  - `web.xml`文件：Web应用程序的配置文件，其中包含Servlet、过滤器、监听器等组件的配置信息。
  - `classes`目录：包含Web应用程序的Java类文件。
  - `lib`目录：包含Web应用程序所需的JAR文件。
- `META-INF`目录：包含Web应用程序的META-INF文件。
  - `MANIFEST.MF`文件：包含Web应用程序的清单信息，例如应用程序名称、版本号等。
- 静态资源目录：通常包含HTML、CSS、JavaScript、图片等文件。
- Java源代码目录：包含Web应用程序的Java源代码文件。

## <font class="text-color-13" color="#ffeb3b">Idea 开发 Servlet 程序</font>
1. 新建 Project

2. 新建 Module

3.  让 Module 变为 javaEE 的模块（让 Module 变成 webapp 的模块，符合 webapp 的规范。符合 Servlet 规范的 Module）
	- 在 Module 上点击右键：Add Framework support（添加框架支持）
	- 选择 Web Application（选择的是 webapp 的支持）
	- Idea 会自动生成一个符合 Servlet 规范的 webapp 目录结构，生成的这个 `web` 目录就代表 webapp 的根
4.  将 tomcat/lib/servlet-api.jar 和 sp-api.jar 添加到 classpath 当中
	- File --> Project Structure --> Modules --> "+" --> Add JARS

5. 实现 jakarta.servlet.Servelt 当中的5个方法

6.  在 Servlet 的 `service` 方法中编写业务代码
```java
package test01;

import jakarta.servlet.*;

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.*;
import java.util.ResourceBundle;

public class EmployeeServlet implements Servlet {
    @Override
    public void init(ServletConfig servletConfig) throws ServletException {

    }

    @Override
    public ServletConfig getServletConfig() {
        return null;
    }

    @Override
    public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
        // 设置响应的内容类型
        servletResponse.setContentType("text/html");
        PrintWriter out = servletResponse.getWriter();
        // 连接数据库
        Connection conn = null;
        PreparedStatement ps = null;
        ResultSet rs = null;
        ResourceBundle bundle = ResourceBundle.getBundle("jdbc");
        String driver = bundle.getString("driver");
        String url = bundle.getString("url");
        String user = bundle.getString("user");
        String password = bundle.getString("password");

        try {
            // 注册驱动
            Class.forName(driver);
            // 获取连接
            conn = DriverManager.getConnection(url,user,password);
            // 获取预编译的数据库操作对象
            String sql = "select ename,sal from emp";
            ps = conn.prepareStatement(sql);
            // 执行 sql
            rs = ps.executeQuery();
            // 处理结果集
            out.print("name , salary" + "<br>" + "--------------" + "<br>");
            while (rs.next()){
                String name = rs.getString("ename");
                int sal = rs.getInt("sal");
                out.print(name + " , " + sal + "<br>");
            }
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        } finally {
            if(rs != null){
                try {
                    rs.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(ps != null){
                try {
                    ps.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(conn != null){
                try {
                    conn.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    @Override
    public String getServletInfo() {
        return null;
    }

    @Override
    public void destroy() {

    }
}
```


7. 在 `WEB-INF` 目录下新建一个子目录 `lib` ，将数据库的驱动 jar 包放在 lib 目录下

8. 在 `web.xml` 文件中完成 `EmployeeServlet` 类的注册
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    <servlet>
        <servlet-name>EmployeeServlet</servlet-name>
        <servlet-class>test01.EmployeeServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>EmployeeServlet</servlet-name>
        <url-pattern>/servlet/employee</url-pattern>
    </servlet-mapping>
</web-app>
```
9. 在 `WEB-INF` 文件夹外面创建一个 html 文件，提供一个超链接
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Student page</title>
</head>
<body>
    <!-- 这里项目名是 web01，无法动态获取，先写死 -->
    <a href="/web01/servlet/employee">employee salary list</a>
</body>
</html>
```
10. 用 IDEA 工具关联 Tomcat 服务器，将 webapp 部署到 Tomcat 服务器当中

	- Project Structure 的 `artifact` 中添加 `web application exploded` 选择 `module`
	- Add Configuration 中添加 Tomcat Server --> local
	- 配置服务器根目录、JRE、虚拟机参数等
	- 在 `Deployment` 中添加 `artifact` ，将下面的 `Application context` 改为 `/项目名`，此处为 /web01

11. 启动 Tomcat 服务器，以 `debug` 模式启动 Tomcat 服务器

12. 在浏览器中，地址栏输入：`http://127.0.0.1:8080/web01/index.html` 即可访问页面

## <font class="text-color-13" color="#ffeb3b">ServletResponse</font>
* ServletResponse接口是Java Servlet API中的一个接口，它用于表示向客户端发送HTTP响应的对象。当Servlet接收到HTTP请求并完成处理后，它将使用ServletResponse接口中的方法构建HTTP响应并将其发送回客户端浏览器。

- 重要方法

| 方法 | 描述 |
| --- | --- |
| `void setContentType(String type)` | 设置响应的MIME类型。例如，可以设置为"text/html"，表示响应是HTML文档。 |
| `PrintWriter getWriter() throws IOException` | 获取一个用于写入响应数据的PrintWriter对象。可以使用这个方法来向客户端发送响应内容，例如HTML页面或JSON数据。 |
| `void setHeader(String name, String value)` | 设置指定名称的响应标头的值。可以使用这个方法来设置响应的内容类型、缓存控制、跨域请求等相关信息。 |
| `void sendRedirect(String location) throws IOException` | 将响应重定向到另一个URL。例如，可以将请求重定向到登录页面或者其他Web页面。 |
| `void setStatus(int sc)` | 设置响应的HTTP状态码。常见的状态码有200、404、500等。可以使用这个方法来表示请求处理的结果状态。 |
| `void setCharacterEncoding(String charset)` | 设置响应的字符编码。例如，可以设置为"UTF-8"。 |
| `int getBufferSize()` | 获取响应的缓冲区大小。 |
| `void setBufferSize(int size)` | 设置响应的缓冲区大小。 |
| `void flushBuffer() throws IOException` | 将缓冲区的响应数据发送到客户端，并清空缓冲区。 |
| `void reset()` | 重置响应的状态。例如，清空响应头和缓冲区。 |
| `void resetBuffer()` | 清空响应的缓冲区。 |

## <font class="text-color-13" color="#ffeb3b">向浏览器响应 html 代码</font>
* 在service()方法中向浏览器发送HTML代码，可以使用ServletResponse接口的getWriter()方法获取一个PrintWriter对象，然后使用PrintWriter的print()或println()方法将HTML代码写入到响应中。
```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class MyServlet extends HttpServlet {
    protected void service(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {

        // 设置响应的内容类型为HTML
        response.setContentType("text/html");

        // 获取PrintWriter对象，用于向响应中写入HTML代码
        PrintWriter out = response.getWriter();

        // 向响应中写入HTML代码
        out.println("<html>");
        out.println("<head><title>MyServlet</title></head>");
        out.println("<body>");
        out.println("<h1>Hello, World!</h1>");
        out.println("</body></html>");
    }
}
```
## <font class="text-color-13" color="#ffeb3b">Servlet 对象的生命周期</font>
- Servlet 对象的生命周期由 web 服务器全权负责。Tomcat 服务器通常又被称为 web 容器。

- 在一个Web应用中，每一个Servlet都有一个唯一的Servlet名称，这个名称在部署描述符（web.xml）中定义。Web容器根据这个Servlet名称来管理Servlet的生命周期。通常，Servlet 对象由Web容器通过内部的数据结构进行管理。

- 在实际的实现中，Web容器可能会使用各种数据结构来跟踪Servlet实例，这主要取决于容器的实现。例如，Web容器可能会使用哈希表（HashMap）或其他类型的映射（Map）数据结构，将Servlet名称（或别的唯一标识）映射到对应的Servlet实例。

### <font class="text-color-15" color="#ff9800">实例化</font>

- Servlet的实例化时间取决于它的加载策略，这通常在Web应用的部署描述符（通常是web.xml文件）中配置。

- Servlet可以被配置为在服务器启动时加载（也被称为预加载或启动时加载），也可以在接收到第一个请求时加载。这是通过在部署描述符中设置Servlet的 `<load-on-startup>` 元素来控制的。

	- 如果设置了 `<load-on-startup>` 元素并为其赋予了一个非负整数值，那么Servlet就会在服务器启动时加载。数字的大小决定了Servlet的加载顺序，数字越小，Servlet越早加载。如果多个Servlet有相同的 `<load-on-startup>` 值，那么它们的加载顺序是未定义的。

	- 如果没有设置 `<load-on-startup>` 元素，或者为其赋予了负数值，那么Servlet会在接收到第一个请求时加载。

	- 例如，如果你有一个名为`ExampleServlet`的Servlet，你可以如下配置它：
```xml
<servlet>
    <servlet-name>ExampleServlet</servlet-name>
    <servlet-class>com.example.ExampleServlet</servlet-class>
    <load-on-startup>1</load-on-startup>
</servlet>
```
### <font class="text-color-141" color="#ff9800">init() 方法</font>

- Servlet的 `init()` 方法在Servlet被实例化后，也就是在Servlet首次加载到内存时执行。这个方法是用于执行任何必要的初始化操作。

	- 当Servlet被配置为在服务器启动时加载（也就是在web.xml中设置了 `<load-on-startup>` 元素），`init()` 方法就会在服务器启动时被调用。如果Servlet被配置为在接收到第一个请求时加载（也就是没有设置 `<load-on-startup>` 元素，或者将其设置为负数），那么 `init()` 方法就会在接收到第一个请求时被调用。

	- 注意，无论Servlet处理多少次请求，`init()` 方法只会被调用一次。

- Servlet对象通常是单例的（假单例）。在Web容器（例如Tomcat）中，对于每一个Servlet类，通常只会创建一个实例。这个实例在接收到第一个请求时（或者在服务器启动时，如果Servlet被配置为在启动时加载）被创建，并在服务器关闭或应用被卸载时被销毁。在这期间，这个Servlet实例可以处理多个请求。

	- 这是因为Servlet是线程安全的，可以同时处理多个请求。当接收到一个新的请求时，Web容器会创建一个新的线程，然后在这个线程中调用Servlet实例的service()方法（或者是doGet()、doPost()等方法，如果Servlet是HttpServlet的子类）。因此，同一个Servlet实例可以同时在多个线程中运行，处理多个请求。

	- 这种设计模式有助于提高服务器的性能，因为创建新的Servlet实例是一个相对昂贵的操作，而创建新的线程则相对便宜。但是，这也意味着在Servlet中，需要小心处理共享的状态，以避免线程安全问题。例如，应该避免在Servlet类中使用实例变量来存储请求或响应的状态，因为这样可能会导致不正确的行为，如果两个线程同时访问和修改这个状态的话。

### <font class="text-color-141" color="#ff9800">service() 方法</font>

- Servlet的 `service()` 方法在每次接收到HTTP请求时被调用。这个方法是负责处理HTTP请求的主要方法。

	- 当Web容器（例如Tomcat）接收到一个针对某个Servlet的请求时，它会创建一个新的线程，然后在这个线程中调用对应Servlet实例的`service()`方法。`service()`方法接收两个参数：一个ServletRequest对象和一个ServletResponse对象。ServletRequest对象包含了关于请求的所有信息，例如请求的参数、请求头和Cookies等，而ServletResponse对象则用于生成响应。

	- 在Servlet的子类HttpServlet中，`service()`方法进一步细分为多个方法，每个方法对应HTTP协议的一个方法。例如，`doGet()`方法处理GET请求，`doPost()`方法处理POST请求，等等。如果你的Servlet是HttpServlet的子类，你通常会覆盖这些方法，而不是`service()`方法，以处理特定类型的请求。

	- 总的来说，`service()`方法在每次接收到请求时被调用，处理请求，并生成响应。这个过程在每次请求时都会重复，直到服务器关闭或应用被卸载。

### <font class="text-color-141" color="#ff9800">destroy() 方法</font>
- Servlet的`destroy()`方法在Servlet的生命周期结束时被调用，用于执行任何必要的清理操作。具体来说，这个方法在以下情况下被调用：

	1. 当Web服务器关闭时。
	2. 当Web应用被从服务器上卸载或重新部署时。
	3. 当Servlet被从Web应用的部署描述符（通常是web.xml文件）中移除时。

- `destroy()`方法只会被调用一次，就像`init()`方法只会在Servlet被初始化时调用一次一样。在`destroy()`方法被调用后，Servlet实例就不再可用，不能再处理任何请求。

	- 在`destroy()`方法中，你可以释放Servlet使用的资源，例如数据库连接、文件句柄或者网络连接等。你也可以用这个方法来保存Servlet的状态，以便在下次启动时恢复。

	- 请注意，虽然`destroy()`方法是在Servlet生命周期结束时被调用的，但是并不能保证它总是被调用。例如，如果Web服务器突然崩溃或被强制关闭，`destroy()`方法可能就无法被调用。因此，你应该尽量避免依赖`destroy()`方法来保存重要的状态或释放关键的资源，而应该尽可能在处理完每个请求后立即进行这些操作。

### <font class="text-color-141" color="#ff9800">Servlet生命周期的简单示例</font>
```java
import javax.servlet.*;
import java.io.IOException;

public class SimpleServlet implements Servlet {

    @Override
    public void init(ServletConfig servletConfig) throws ServletException {
        System.out.println("Servlet is being initialized");
    }

    @Override
    public ServletConfig getServletConfig() {
        return null;
    }

    @Override
    public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
        servletResponse.getWriter().println("Hello, World!");
    }

    @Override
    public String getServletInfo() {
        return "SimpleServlet";
    }

    @Override
    public void destroy() {
        System.out.println("Servlet is being destroyed");
    }
}
```
- 在这个例子中：

	1. `init()` 方法在Servlet被初始化时调用，这里只是简单地打印一条消息。
	2. `service()` 方法在接收到请求时被调用，这里返回一个简单的"Hello, World!"消息。
	3. `destroy()` 方法在Servlet被销毁时调用，这里也只是打印一条消息。

- 此外，还实现了 `getServletConfig()` 和 `getServletInfo()` 方法，这两个方法是Servlet接口的一部分，必须在每个Servlet类中实现。这里 `getServletConfig()` 返回 null，`getServletInfo()` 返回一个简单的字符串，实际的Servlet可能会有更复杂的实现。
