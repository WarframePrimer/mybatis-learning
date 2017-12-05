
# 原生JDBC的步骤
- 1.加载数据库驱动(Class.forName(className)) 
- 2.创建并获取数据库连接(DriverManager.getConnection(url,user,password))
- 3.创建JDBC Statement对象
- 4.sql语句
- 5.设置sql语句中的参数(当使用preparedStatement的时候)
- 6.通过Statement(Statement是preparedStatement的父接口)执行sql获取结果
- 7.对sql执行结果进行解析处理(比如ResultSet)
- 8.释放资源(resultSet、preparedStatement、connection)

存在的问题：
- 1.数据库连接，使用是就创建，不使用立即释放，对数据库进行频繁连接开启和关闭，造成数据库资源的浪费，也影响性能。   
    `考虑使用数据库连接池管理数据库连接。`
- 2.将sql语句硬编码到java代码中，如果sql语句修改，需要重新编译java代码，不利于系统维护。   
    `将sql语句配置到xml配置文件中，即使sql变化，不需要对java代码进行重新编译。` 
- 3.向preparedStatement中设置参数，对占位符号位置和设置参数值，硬编码在java代码中，不利于系统维护。  
     `将sql语句及占位符号和参数全部配置到xml中。`
- 4.从resultSet中遍历结果集数据时，存在硬编码，将获取表的字段进行硬编码，不利于系统维护。  
     `将查询到的结果集，自动映射成java对象。`
