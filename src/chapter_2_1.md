# 执行流程

MyBatis的执行流程可以分为以下几个步骤：

1. 加载配置文件

MyBatis通过读取配置文件（mybatis-config.xml）来获取数据库连接信息、插件、映射文件等配置信息。

2. 构建 SqlSessionFactory

通过 SqlSessionFactoryBuilder 类来读取配置文件，创建 SqlSessionFactory 实例。SqlSessionFactory 是 MyBatis 的核心组件之一，用于创建 SqlSession 实例。

3. 打开 SqlSession

通过 SqlSessionFactory 的 openSession() 方法来创建 SqlSession 实例。SqlSession 是 MyBatis 的另一个核心组件，用于执行 SQL 语句。

4. 加载 Mapper 映射文件

通过 SqlSession 的 getMapper() 方法来获取 Mapper 接口的代理对象。MyBatis 会自动查找与 Mapper 接口同名的 XML 映射文件，并根据映射文件中的配置信息生成 Mapper 接口的实现类。这个过程中，MyBatis会使用动态代理技术，生成 Mapper 接口的代理对象。

5. 执行 SQL 语句

通过 Mapper 接口的方法来执行 SQL 语句。MyBatis会根据方法名和参数类型来查找对应的 SQL 语句，并执行 SQL 语句。执行结果会被封装成 Java 对象或者 Java 集合返回给调用方。

6. 关闭 SqlSession

在完成对数据库的操作后，需要关闭 SqlSession，释放资源。可以通过调用 SqlSession 的 close() 方法来关闭 SqlSession 实例。

_总结_

在完成对数据库的操作后，需要关闭 SqlSession，释放资源。可以通过调用 SqlSession 的 close() 方法来关闭 SqlSession 实例。

总的来说，MyBatis的执行流程相对简单，通过读取配置文件、构建 SqlSessionFactory、打开 SqlSession、加载 Mapper 映射文件、执行 SQL 语句和关闭 SqlSession 这几个步骤来完成对数据库的操作。MyBatis的核心组件 SqlSessionFactory、SqlSession 和 Mapper 都是通过工厂模式和代理模式来实现的，这也是 MyBatis具有高灵活性和可扩展性的重要原因之一。

## 源码理解
