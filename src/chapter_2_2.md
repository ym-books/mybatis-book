# 执行一次SQL过程

mybatis执行一次sql的过程如下：

1. 通过 SqlSessionFactory 创建 SqlSession 实例。
```java
SqlSessionFactory sqlSessionFactory = ...
SqlSession sqlSession = sqlSessionFactory.openSession();

```
2. 通过 SqlSession 的 getMapper() 方法获取 Mapper 接口的代理对象。
```java
MyMapper mapper = sqlSession.getMapper(MyMapper.class);

```
3. 调用 Mapper 接口的方法执行 SQL 语句。
```java
List<User> userList = mapper.getUserList();

```
4. MyBatis 解析 SQL 语句并生成对应的 PreparedStatement 对象。
```java
MappedStatement mappedStatement = configuration.getMappedStatement(statement);
BoundSql boundSql = mappedStatement.getBoundSql(parameterObject);
PreparedStatement statement = connection.prepareStatement(boundSql.getSql());

```
5. 将 SQL 参数设置到 PreparedStatement 对象中。
```java
parameterHandler.setParameters(statement);

```
6. 执行 SQL 语句并获取结果集。
```java
ResultSet rs = statement.executeQuery();

```
7. MyBatis 将结果集转换为 Java 对象。
```java
resultSetHandler.handleResultSets(statement);

```
8. 关闭 PreparedStatement 对象。
```java
statement.close();

```
9. 关闭 SqlSession 对象。
```java
sqlSession.close();

```

总体来说，MyBatis 执行 SQL 语句的过程比较复杂，但大致可以分为三个阶段：
1. 解析 SQL 语句并生成 PreparedStatement 对象。
2. 将 SQL 参数设置到 PreparedStatement 对象中并执行 SQL 语句。
3. 将结果集转换为 Java 对象并返回给调用方。

在这个过程中，MyBatis使用了一系列的设计模式和技术，如工厂模式、代理模式、装饰器模式、反射等，以实现 MyBatis 的高灵活性和可扩展性。
