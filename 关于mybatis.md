
# mybatis介绍  
    mybatis是一个持久层的框架，是apache下的顶级项目。   
    mybatis让程序将主要精力放在sql上，通过mybatis提供的映射方式，自由灵活生成满足需求的sql语句。  
    mybatis可以将向preparedStatement中的输入参数自动进行输入映射，将查询结果集灵活映射成java对象(输出映射)。  


## 框架原理  

### mybatis框架执行过程  
- 1.配置mybatis的配置文件，SqlMapConfig.xml(名称任意)
- 2.通过配置文件，加载mybatis运行环境，创建SqlSessionFactory(单例)
- 3.通过SqlSessionFactory创建SqlSession。SqlSession是一个面向用户的接口(提供操作数据库方法)，实现对象是非线程安全的，所以sqlSession应用场合应该在方法体内。
- 4.调用sqlSession的方法去操作数据。如果需要提交事务，需要执行SqlSession的commit方法。
- 5.释放资源，关闭sqlSession。

### mybatis开发dao的方法
- 1.原始dao的方法   
    a.需要程序员自己编写dao接口和实现类  
    b.需要在dao实现类中注入SqlSessionFactory工厂  
- 2.mapper代理  
    只需要程序员编写mapper接口(dao接口)。程序员在编写mapper.xml(映射文件)和mapper接口是需要遵循一个开发规范：  
        a.mapper.xml中namespace就是对应mapper接口的类全路径  
        b.mapper.xml中statement的id和对应mapper接口中的方法名要一致  
        c.mapper.xml中statement的parameterType指定输入参数的类型和对应mapper接口方法输入参数类型保持一致  
        d.mapper.xml中statement的resultType指定输出结果的类型和对应接口中的方法返回值保持一致  
    `SqlMapConfig.xml配置文件:配置properties属性、别名、mapper加载`。  
### 输入映射和输出映射
- 输入映射：    
    parameterType:指定输入参数类型可以为简单类型、pojo、hashmap。  
    对于综合查询，建议parameterType使用包装的pojo，有利于系统扩展。  
- 输出映射：  
    resultType:查询到的列名和resultType指定的pojo中的属性名一致才能映射成功。  
    resultMap:可以通过resultMap完成一些高级映射。如果查询到的列名和映射的pojo的属性名不一致，通过resultMap设置列名和属性名之间的对应关系就可以完成映射  
  

        


  
