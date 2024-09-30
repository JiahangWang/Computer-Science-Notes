# <center>JDBC</center>

[数据库连接器驱动下载](https://blog.csdn.net/Cryhelyxx/article/details/39502937)

## <font class="text-color-13" color="#ffeb3b">概述</font>
* https://blog.csdn.net/fuhanghang/article/details/124247439

* JDBC (Java Database Connectivity) 是一种Java编程语言的API（Application Programming Interface），用于与各种关系型数据库进行交互。通过JDBC，开发人员可以编写Java应用程序，与不同的数据库进行通信，从而对数据库进行查询、更新等操作。JDBC的API是Java SE的一部分，因此它不需要额外的安装或配置。JDBC主要用于开发Java Web应用程序和其他Java应用程序，可以实现与Oracle、MySQL、SQL Server等各种主流数据库之间的交互。

* 驱动：所有数据库的驱动都是以 jar 包的形式存在，jar 包中有很多 .class 文件，这些 class 文件就是对 JDBC 接口的实现。驱动不是 SUN 公司提供的，是数据库厂商负责提供。

## <font class="text-color-121" color="#ffeb3b">JDBC 编程步骤</font>
1. 注册驱动（告诉 java 程序，即将要连接哪个品牌的数据库）
2. 获取连接（表示 JVM 的进程和数据库进程之间的通道打开了，这属于进程之间的通信，使用之后需关闭通道）
3. 获取数据库操作对象（执行 SQL 语句的对象）
4. 执行 SQL 语句（DQL，DML...）
5. 释放资源（java 和数据库属于进程间的通信，开启后一定要关闭）

```java
        Connection conn = null;
        Statement stmt = null;

        try {
            // 1.注册驱动
                // 第一种方式
            DriverManager.registerDriver(new com.mysql.jdbc.Driver());
                // 第二种方式（通过类加载，更常用）
            Class.forName("com.mysql.jdbc.Driver");
            // 2.获取连接
            String url = "jdbc:mysql://127.0.0.1:3306/mydb";
            String username = "root";
            String password = "12345";
            conn = DriverManager.getConnection(url, username, password);
            System.out.println(conn);
            // 3.获取数据库操作对象
            stmt = conn.createStatement();
            // 4.执行sql
            String sql = "insert into t_student (no,name,age,sex,email) values(323,'Tom',34,'male','Tom@gmail.com')";
            int count = stmt.executeUpdate(sql);
            System.out.println(count == 1 ? "插入成功" : "插入失败");
            //5.处理结果查询结果集

        } catch (SQLException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            throw new RuntimeException(e);
        } finally {
            // 6.释放资源（按顺序关闭）
            if(stmt != null) {
                try {
                    stmt.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(conn != null) {
                try {
                    conn.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }
```

### <font class="text-color-15" color="#ff9800">相关方法</font>
* public Connection <font class="text-color-101" color="#8bc34a">getConnection</font>(String url, String user, String password) throws SQLException ：用于建立数据库连接，返回一个 Connection 对象。

* public static void <font class="text-color-101" color="#8bc34a">registerDriver</font>(Driver driver) throws SQLException ：DriverManager类的一个静态方法，用于注册给定的驱动程序。 驱动程序应该在应用程序中的静态初始化块中注册，或者在第一次使用它之前注册。

* public int <font class="text-color-11" color="#8bc34a">executeUpdate</font>(String sql) throws SQLException ：该方法用于执行 SQL 语句，并返回受影响的行数（即执行 INSERT、UPDATE 或 DELETE 等语句后受影响的行数）。（用于执行 DML 语句）

### <font class="text-color-15" color="#ff9800">URL概述</font>
* URL（Uniform Resource Locator）即统一资源定位符，是用于指定互联网上资源位置的地址。通常情况下，URL包括协议（例如HTTP、FTP、SMTP等）、服务器地址、资源路径等信息，用于定位网络上的资源，例如网页、图像、视频等。
```
protocol://hostname[:port]/path/[?query][#fragment]
```
* 其中：
	protocol：指定使用的协议，例如HTTP、FTP等；
	hostname：指定主机名或IP地址，例如www.example.com或192.168.0.1；
	port：指定端口号，例如80或443，默认端口可以省略；
	path：指定资源路径，例如/index.html或/images/logo.png；
	query：指定查询参数，例如?key1=value1&key2=value2；
	fragment：指定文档片段，例如#section1。
	
* URL可以用于访问网页、下载文件、发送电子邮件等各种网络操作。在Web开发中，URL也常用于构建RESTful API接口。

## <font class="text-color-121" color="#ffeb3b">属性配置文件连接数据库</font>
* 将连接数据库的所有信息配置到属性配置文件当中
```java
        // 使用资源绑定器获取属性配置文件
        ResourceBundle bundle = ResourceBundle.getBundle("jdbc");
        String driver = bundle.getString("driver");
        String url = bundle.getString("url");
        String user = bundle.getString("user");
        String password = bundle.getString("password");
        
        Connection conn = null;
        Statement stmt = null;

        try {
            Class.forName(driver);
            conn = DriverManager.getConnection(url,user,password);
            stmt = conn.createStatement();
            
            stmt.executeUpdate("insert into t_user (Id, Name, City) VALUES (001,'Tom','Chengdu')");
			stmt.executeUpdate("update t_user set City = 'Shanghai' where id = 002");
            
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } catch (SQLException e) {
            e.printStackTrace();
        }finally {
            if(stmt != null) {
                try {
                    stmt.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(conn != null) {
                try {
                    conn.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }
```
* 实际开发中不建议吧连接数据库的信息写死到 java 程序中
* 属性配置文件示例：
```properties
driver=com.mysql.jdbc.Driver
url=jdbc:mysql://127.0.0.1:3306/db01
user=root
password=12345
```


## <font class="text-color-121" color="#ffeb3b">处理查询结果集</font>
### <font class="text-color-15" color="#ff9800">相关方法</font>
* ResultSet <font class="text-color-101" color="#8bc34a">executeQuery</font>(String sql) throws SQLException ： 该方法用于执行一个查询操作并返回一个 ResultSet 对象，封装了执行 SQL 查询语句的结果。如果执行的 SQL 查询语句不返回任何结果集，则该方法返回 null。（用于执行 DQL 语句）

* boolean <font class="text-color-101" color="#8bc34a">next</font>() ：移动光标到此ResultSet对象的下一行，如果有行则返回true，否则返回false。

* String <font class="text-color-101" color="#8bc34a">getString</font>(int columnIndex) throws SQLException ：该方法用于从当前结果集中检索指定列的值，并将其作为字符串返回。参数columnIndex指定要检索的列的索引，第一列的索引为1，第二列为2，以此类推。如果该列的值为null，则返回null。如果该列的值为字符类型，则返回该字符类型的字符串表示形式。如果该列的值为数字类型，则将其转换为字符串。如果该列的值为日期/时间类型，则将其转换为字符串形式，该字符串格式取决于JDBC驱动程序的实现。如果该列的值为二进制类型，则返回其十六进制字符串表示形式。如果结果集已关闭，则抛出SQLException。

* int <font class="text-color-101" color="#8bc34a">getInt</font>(String columnLabel) throws SQLException ：从当前行中获取指定列的值作为int类型。列可以使用列名或列索引来指定。如果列的值为null，则返回0。如果列的值不能转换为int类型，则会抛出SQLException异常。

* public double <font class="text-color-101" color="#8bc34a">getDouble</font>(int columnIndex) throws SQLException ：该方法用于从当前行中获取指定列的 double 类型的值。该方法接受一个 int 类型的参数 columnIndex，表示需要获取值的列的编号（从 1 开始）。如果指定列的值为 null，则该方法返回 0.0。如果指定列的值不是 double 类型，则该方法会抛出 SQLException 异常。

* 注：除了传入列的序号（int），也可以传入查询结果对应的列名（String）
```java
        // 使用资源绑定器获取属性配置文件
        ResourceBundle bundle = ResourceBundle.getBundle("jdbc");
        String driver = bundle.getString("driver");
        String url = bundle.getString("url");
        String user = bundle.getString("user");
        String password = bundle.getString("password");

        Connection conn = null;
        Statement stmt = null;
        ResultSet rs = null;

        try {
            Class.forName(driver);
            conn = DriverManager.getConnection(url,user,password);
            stmt = conn.createStatement();

            // 执行查询
            rs = stmt.executeQuery("select * from t_user");
            // 处理查询结果集
            while (rs.next()) {
                StringBuffer res = new StringBuffer();
                res.append(rs.getInt(1) + " ");
                res.append(rs.getString("name") + " ");
                res.append(rs.getString("city") + " ");
                res.append(rs.getInt("sal") + 250);
                System.out.println(res);
            }

        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } catch (SQLException e) {
            e.printStackTrace();
        }finally {
            if(rs != null) {
                try {
                    rs.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(stmt != null) {
                try {
                    stmt.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(conn != null) {
                try {
                    conn.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }

```

## <font class="text-color-121" color="#ffeb3b">SQL 注入</font>

### <font class="text-color-15" color="#ff9800">存在问题的登录系统</font>
```java
public class LoginUI {

    public static Map<String, String> initUI(){
        Scanner scanner = new Scanner(System.in);
        System.out.print("用户名：");
        String loginName = scanner.nextLine();
        System.out.print("密码：");
        String loginPassword = scanner.nextLine();
        Map<String,String> userLoginMap = new HashMap<>();
        userLoginMap.put("loginName",loginName);
        userLoginMap.put("loginPassword",loginPassword);
        return userLoginMap;
    }

}
```
```java
public class LoginDB {
    public static boolean login(Map<String, String> userLoginMap){
        boolean loginSuccess = false;

        ResourceBundle bundle = ResourceBundle.getBundle("UserLogin/loginDB");
        String driver = bundle.getString("driver");
        String url = bundle.getString("url");
        String user = bundle.getString("user");
        String password = bundle.getString("password");

        String loginName = userLoginMap.get("loginName");
        String loginPassword = userLoginMap.get("loginPassword");

        Connection conn = null;
        Statement stmt = null;
        ResultSet rs = null;

        try {
            // 注册驱动
            Class.forName(driver);
            // 获取连接
            conn = DriverManager.getConnection(url,user,password);
            // 获取数据库操作对象
            stmt = conn.createStatement();
            String sql = "select * from t_user where loginName = '"+loginName+"' and loginPwd = '"+loginPassword+"'";
            // 以上完成了 sql 语句的拼接，以下发送 sql 语句给 DBMS，DBMS 进行 sql 编译
            ResultSet resultSet = stmt.executeQuery(sql);
            // 处理结果集
            if(resultSet.next()) loginSuccess = true;

        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } catch (SQLException e) {
            e.printStackTrace();
        }finally {
            if(rs != null) {
                try {
                    rs.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(stmt != null) {
                try {
                    stmt.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(conn != null) {
                try {
                    conn.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }

        return loginSuccess;
    }
}
```
```java
public class UserLogin {
    public static void main(String[] args) {
        // 获取用户名和密码信息
        Map<String,String> userLoginMap = LoginUI.initUI();
        // 验证用户名和密码
        Boolean loginSuccess = LoginDB.login(userLoginMap);
        // 输出结果
        System.out.println(loginSuccess? "登录成功" : "登录失败");
    }
}
```
* 不存在的用户名登陆成功
* 拼接后的 sql 语句：(and 优先级大于 or)
```select * from t_user where loginName = 'qsn' and loginPwd = 'qsn' or '1'='1'```
```
用户名：qsn
密码：qsn' or '1'='1
登录成功
```
### <font class="text-color-15" color="#ff9800">概念</font>
* SQL注入是一种攻击技术，攻击者利用输入参数中嵌入SQL命令来篡改数据库中的数据或者获取敏感信息。SQL注入的主要原因是未能对输入的数据进行充分的过滤和验证，导致攻击者可以在输入框中注入恶意SQL语句，从而执行非法的数据库操作。

* 在应用程序中，如果没有对用户输入的数据进行合适的验证和过滤，那么攻击者可以通过在输入框中注入恶意的SQL语句来执行任意的数据库操作，例如：删除数据库中的表、读取敏感数据等等。此外，如果应用程序使用了拼接字符串的方式来构建SQL语句，而没有使用参数化查询，也容易导致SQL注入攻击。

* SQL注入攻击是一种常见的安全漏洞，开发人员应该在应用程序中采用有效的输入验证和过滤措施，同时使用参数化查询来避免SQL注入攻击。

### <font class="text-color-15" color="#ff9800">解决办法</font>
* 只要用户提供的信息不参与 sql 语句的编译过程，问题就解决了。即使用户提供的信息中含有 sql 语句的关键词，但是没有参与编译，不起作用。

* 要想用户信息不参与 sql 语句的编译，必须使用 java.sql.PreparedStatement
	该接口继承了 java.sql.Statement.
	PreparedStatement 属于预编译的数据库操作对象
	原理：预先对 sql 语句的框架进行编译，然后再给 sql 语句传值

* 改进后的 LoginDB
```java
public class LoginDB {
    public static boolean login(Map<String, String> userLoginMap){
        boolean loginSuccess = false;

        ResourceBundle bundle = ResourceBundle.getBundle("UserLogin02/loginDB");
        String driver = bundle.getString("driver");
        String url = bundle.getString("url");
        String user = bundle.getString("user");
        String password = bundle.getString("password");

        String loginName = userLoginMap.get("loginName");
        String loginPassword = userLoginMap.get("loginPassword");

        Connection conn = null;
        // 使用 PreparedStatement (预编译的数据库操作对象)
        PreparedStatement pstmt = null;
        ResultSet rs = null;

        try {
            // 注册驱动
            Class.forName(driver);
            // 获取连接
            conn = DriverManager.getConnection(url,user,password);
            // 获取预编译的数据库操作对象
                // sql 语句框架， ? 表示占位符，不能加单引号
            String sql = "select * from t_user where loginName = ? and loginPwd = ?";
            pstmt = conn.prepareStatement(sql);
            // 给占位符 ? 传值 （第一个?下标是1，一次类推。JDBC中所有下标从1开始）
            pstmt.setString(1,loginName);
            pstmt.setString(2,loginPassword);
            // 执行 sql
            ResultSet resultSet = pstmt.executeQuery();
            // 处理结果集
            if(resultSet.next()) loginSuccess = true;

        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } catch (SQLException e) {
            e.printStackTrace();
        }finally {
            if(rs != null) {
                try {
                    rs.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(pstmt != null) {
                try {
                    pstmt.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if(conn != null) {
                try {
                    conn.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }

        return loginSuccess;
    }
}
```
### <font class="text-color-15" color="#ff9800">相关方法</font>
* PreparedStatement <font class="text-color-11" color="#8bc34a">prepareStatement</font>(String sql) throws SQLException ：
	prepareStatement 方法是 Connection 接口定义的一个方法，用于将给定的 SQL 语句编译为一个 PreparedStatement 对象。PreparedStatement 对象可以用来多次执行 SQL 语句并填充参数，可以有效地防止 SQL 注入攻击。在执行 SQL 语句前需要使用该方法预编译 SQL 语句，然后通过设置参数的值来执行 SQL 语句。执行时可以多次使用同一个 PreparedStatement 对象，提高了 SQL 语句的执行效率。该方法抛出 SQLException 异常，需要进行异常处理。

* void <font class="text-color-101" color="#8bc34a">setString</font>(int parameterIndex, String x) throws SQLException ：
	setString 方法是 PreparedStatement 接口定义的一个方法，用于设置 SQL 语句中指定位置的参数为指定的字符串值。该方法需要传入两个参数：parameterIndex 表示参数的位置，x 表示要设置的字符串值。该方法支持 Unicode 字符串，并且可以设置 NULL 值。需要注意的是，parameterIndex 的位置从 1 开始而不是从 0 开始。如果给定的参数位置超出了 SQL 语句中参数的个数，则会抛出 SQLException 异常。该方法还支持其他数据类型的设置，如 setInt、setDouble 等，方法签名略有不同。在使用 PreparedStatement 对象执行 SQL 语句前需要使用该方法设置参数值。

* void <font class="text-color-101" color="#8bc34a">setInt</font>(int parameterIndex, int x) throws SQLException ：
setInt 方法是 PreparedStatement 接口定义的一个方法，用于设置 SQL 语句中指定位置的参数为指定的整数值。该方法需要传入两个参数：parameterIndex 表示参数的位置，x 表示要设置的整数值。该方法支持设置 NULL 值。需要注意的是，parameterIndex 的位置从 1 开始而不是从 0 开始。如果给定的参数位置超出了 SQL 语句中参数的个数，则会抛出 SQLException 异常。该方法还支持其他数据类型的设置，如 setString、setDouble 等，方法签名略有不同。在使用 PreparedStatement 对象执行 SQL 语句前需要使用该方法设置参数值。

#### <font class="text-color-7" color="#03a9f4">Statement 和 PreparedStatement 区别</font>
* 参数绑定方式不同
	Statement执行SQL语句时，需要将所有参数直接拼接到SQL语句中。而PreparedStatement可以使用占位符（？）来代替参数，参数值在执行语句之前使用setXXX()方法进行绑定。

* 执行效率不同
	由于Statement在执行SQL语句时需要将所有参数直接拼接到SQL语句中，所以对于重复执行相同语句的情况，PreparedStatement会更快，因为它可以预编译SQL语句并缓存它的执行计划。

* 防止SQL注入攻击
	由于PreparedStatement使用占位符绑定参数值，而不是直接将参数拼接到SQL语句中，因此可以更好地防止SQL注入攻击。因为在使用占位符时，任何不正确的输入都将被视为参数值，而不是SQL语句的一部分。
	
## <font class="text-color-121" color="#ffeb3b">JDBC 的事务机制</font>
* JDBC 中的事务是自动提交的，只要执行任意一条 DML 语句，则自动提交一次。

* 在 JDBC 中，当一个连接被创建时，它默认的自动提交模式是开启的（即 autoCommit = true）。这意味着，每一次执行 SQL 语句都会立即将结果提交到数据库中。如果需要禁用自动提交，可以通过 Connection.setAutoCommit(false) 方法来实现。
### <font class="text-color-15" color="#ff9800">相关方法</font>
* void <font class="text-color-11" color="#8bc34a">setAutoCommit</font>(boolean autoCommit) ：设置连接的自动提交模式。当一个连接被创建时，它的自动提交模式默认是开启的（即 autoCommit = true）。如果自动提交被开启，每一次执行 SQL 语句都会立即将结果提交到数据库中。如果自动提交被禁用（即 autoCommit = false），则需要手动调用 commit() 方法提交事务，或者调用 rollback() 方法回滚事务。

* void <font class="text-color-101" color="#8bc34a">commit</font>() ：提交当前事务，使之生效。在手动提交模式下，当需要将多个 SQL 语句作为一个事务来执行时，需要手动调用 commit() 方法将事务提交到数据库中。如果某一个 SQL 语句执行失败，整个事务将被回滚。在 commit() 方法执行成功后，连接会自动恢复到自动提交模式。

* void <font class="text-color-101" color="#8bc34a">rollback</font>() ：回滚当前事务，取消之前所有未提交的修改。在手动提交模式下，当需要将多个 SQL 语句作为一个事务来执行时，如果某一个 SQL 语句执行失败，整个事务需要回滚。此时，可以通过调用 rollback() 方法来回滚之前的所有修改，恢复到事务开始前的状态。

### <font class="text-color-15" color="#ff9800">账户转账演示事务</font>
```java
public class Transfer {
    public static void main(String[] args) {
        ResourceBundle bundle = ResourceBundle.getBundle("AccountTransfer/account");
        String driver = bundle.getString("driver");
        String url = bundle.getString("url");
        String user = bundle.getString("user");
        String password = bundle.getString("password");

        Connection conn = null;
        PreparedStatement pstmt = null;

        try {
            Class.forName(driver);
            conn = DriverManager.getConnection(url, user, password);
            // 将自动提交机制设置为手动提交：
            conn.setAutoCommit(false); // 开启事务

            String sql = "update t_act set balance = ? where actno = ?";
            pstmt = conn.prepareStatement(sql);

            int count = 0;

            pstmt.setDouble(1,1000);
            pstmt.setInt(2,100001);
            count = pstmt.executeUpdate();


            pstmt.setDouble(1,1000);
            pstmt.setInt(2,100002);
            count += pstmt.executeUpdate();

            System.out.println(count == 2? "转账成功" : "转账失败");
            // 执行到这里说明没有出现异常，事务结束，手动提交数据
            conn.commit(); // 提交事务

        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        } catch (Exception e){
            // 回滚事务
            if(conn != null) {
                try {
                    conn.rollback();
                } catch (SQLException ex) {
                    e.printStackTrace();
                }
            }
            e.printStackTrace();
        }finally {
            if(pstmt != null) {
                try {
                    pstmt.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if( conn != null) {
                try {
                    conn.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }


    }
}
```

## <font class="text-color-121" color="#ffeb3b">工具类封装</font>
```java
public class DButil{

    private DButil() {}

    // 类加载时注册驱动（只执行一次）
    static {
        try {
            Class.forName("com.mysql.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }

    /**
     * 传入属性配置文件路径（要求有 url，user，password 属性字段）,获取数据库连接对象
     *
     * @param propertyFile 属性配置文件路径
     * @return 连接对象 connection
     * @throws SQLException the sql exception
     */
    public static Connection getConnection(String propertyFile) throws SQLException {
        ResourceBundle bundle = ResourceBundle.getBundle(propertyFile);
        String url = bundle.getString("url");
        String user = bundle.getString("user");
        String password = bundle.getString("password");
        Connection conn = DriverManager.getConnection(url,user,password);
        return conn;
    }

    /**
     * 关闭数据库资源
     *
     * @param conn 连接对象
     * @param stmt 数据库操作对象
     * @param rs   结果集
     */
    public static void closeResource(Connection conn, Statement stmt, ResultSet rs){
        if(rs != null) {
            try {
                rs.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        if(stmt != null) {
            try {
                stmt.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        if(conn != null) {
            try {
                conn.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }

}
```
### <font class="text-color-15" color="#ff9800">测试封装</font>
* 模糊查询
```java
public class Test_2 {
    public static void main(String[] args) {
        Connection conn = null;
        PreparedStatement stmt = null;
        ResultSet rs = null;

        try {
            conn = DButil.getConnection("jdbc");
            String sql = "select * from t_user where Name like ?";
            stmt = conn.prepareStatement(sql);

            stmt.setString(1,"_o%");

            rs = stmt.executeQuery();

            // 处理查询结果集
            while (rs.next()) {
                System.out.println(rs.getString(2));
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }finally {
            DButil.closeResource(conn,stmt,rs);
        }
    }
}
```






