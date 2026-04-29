# Agenda
1. [Comparison of Approaches](#comparison-of-database-connection-and-query-execution-approaches-in-spring)
2. [Real-World Recommendation](#real-world-recommendation-senior-level-thinking)
3. Implementation JDBC
4. Implementation JdbcTemplate
5. Implementation JPA
6. Implementation Hibernate
7. Implementation NamedParameterJdbcTemplate
8. Implementation Spring Data JDBC
9. Implementation jOOQ
10. Implementation R2DBC
11. Implementation Combine Approaches - JPA, JdbcTemplate, HikariCP
12. Multiple database connections and transactions

### Comparison of Database Connection and Query Execution Approaches in Spring

| **Approach** | **Performance** | **Control** | **Complexity** | **Best Use Case** | **How it work**                                 | ** Core Concept**         |
|---|---|---|---|---|-------------------------------------------------|---------------------------|
| **JDBC** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ❌ High | Low-level work | You manually create connection and execute SQL. | JDBC                      |
| **JdbcTemplate** | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⚖️ Medium | Fast + SQL control | Spring wraps JDBC and removes boilerplate.| Spring JdbcTemplate       |
| **JPA** | ⭐⭐ | ⭐ | ⭐ Easy | CRUD apps |Uses ORM to map Java objects ↔ tables<br/>Performance issues (N+1 problem) | Spring Data JPA <br/>Hibernate |
| **Hibernate** | ⭐⭐ | ⭐⭐ | ❌ Medium | Custom ORM |You directly use ORM without Spring Data abstraction.|
|**NamedParameterJdbc<br/>Template** | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⚖️ Medium | SQL with named params | Like JdbcTemplate but supports named parameters. | Spring NamedParameterJdbcTemplate |
|**Spring Data JDBC**| ⭐⭐⭐ | ⭐⭐ | ⚖️ Medium | Simple SQL + Spring Data features | Like JPA but without ORM. Maps directly to tables. | Spring Data JDBC |
| **jOOQ** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ❌ Medium | Complex SQL |Write SQL in a type-safe Java DSL| | jOOQ |
| **R2DBC** | ⭐⭐⭐⭐ | ⭐⭐⭐ | ❌ High | Reactive apps |Non-blocking DB access| | Reactive Relational Database Connectivity (R2DBC) |


### 💡 **Real-World Recommendation (Senior-level thinking)**

In production systems, people often combine approaches:

Use JPA → for normal CRUD

Use JdbcTemplate / jOOQ → for complex queries

Use HikariCP → for connection pooling

👉 **This hybrid approach gives:**

Clean code (JPA)

Performance (SQL tools)

Scalability

### Implementation JDBC

1. Dependency
```xml
<dependency>
    <groupId>com.oracle.database.jdbc</groupId>
    <artifactId>ojdbc11</artifactId>
    <scope>runtime</scope>
</dependency>
```

2. Configure Database Connection
```java
   String url = "jdbc:mysql://localhost:3306/sampleapi";
   String user = "root";
   String password = "password";
``` 

3. Get Connection
   Two ways:
- DriverManager
```java
Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/testdb",
    "root",
    "password");
```   
❌ Problem

Creates a new connection every time

Expensive (slow in production)

- DataSource (Correct Approach)
```java
DataSource dataSource; // injected or configured

Connection con = dataSource.getConnection();
```
    
4. Create Query
```java
String sql = "SELECT id, name FROM users WHERE id = ?";
PreparedStatement ps = con.prepareStatement(sql);
ps.setInt(1, 1);
```

5. Execute Query
```java
ResultSet rs = ps.executeQuery(); 
```
6. Map results manually
```java
 while (rs.next()) {
   int id = rs.getInt("id");
   String name = rs.getString("name");
   System.out.println(id + " " + name);
}
```
7. Close resources
```java
finally {
    if (rs != null) rs.close();
    if (ps != null) ps.close();
    if (con != null) con.close();
}
```

😵‍💫 Problems with Raw JDBC
1. Boilerplate code
   try/catch/finally everywhere
2. Manual resource management
   Forget to close → memory leak
3. Manual mapping
   user.setName(rs.getString("name"));
4. No transaction management
   You must handle commit/rollback
   con.setAutoCommit(false);
   con.commit();
   con.rollback();
   ⚡ 4. Why It Still Matters

Even if you use Spring:

Spring JdbcTemplate → wraps JDBC
Hibernate → uses JDBC internally

👉 So understanding JDBC = understanding everything beneath

### Implementation JdbcTemplate

It removes:

* manual connection handling
* try/catch/finally
* ResultSet mapping boilerplate

👉 You only write:

* SQL
* mapping logic

1. Dependency
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jdbc</artifactId>
</dependency>
```

2. Database Configurations
```properties
spring.datasource.url=jdbc:oracle:thin:@//localhost:1521/ORCLPDB1
spring.datasource.username=system
spring.datasource.password=password
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
```
👉 Spring Boot auto-creates:

* DataSource
* JdbcTemplate

3. Model Class
```java 
public class User {
    private Long id;
    private String name;

    // getters & setters
} 
```
4. Repository Layer

--READ (single)
```java
public Users findById(String id) {

        String sql ="SELECT * FROM users WHERE id = ?";

        Object[] params = new Object[]{id};

        RowMapper<Users> rowMapper = (rs, rowNum) -> {
            Users u = new Users();
            u.setId(rs.getInt("id"));
            u.setName(rs.getString("name"));
            u.setEmail(rs.getString("email"));
            return u;
        };
    return jdbcTemplate.queryForObject(sql, params,rowMapper);

}
```