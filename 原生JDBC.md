
# 原生JDBC的步骤
- 1.加载数据库驱动(Class.forName(...)) 
- 2.创建并获取数据库连接(DriverManager.getConnection(...))
- 3.创建JDBC Statement对象
- 4.sql语句
- 5.设置sql语句中的参数(当使用prepareStatement的时候)
- 6.通过Statement(Statement是prepareStatement的父接口)执行sql获取结果
- 7.对sql执行结果进行解析处理(比如ResultSet)
- 8.释放资源(resultSet、prepareStatement、connection)

存在的问题：
- 
