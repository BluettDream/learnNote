## 创建db文件
```shell
sqlite3 dbname.db
```

## springboot集成sqlite和druid
```yaml
spring:
  datasource:
    url: jdbc:sqlite:lib/asir.db
    driver-class-name: org.sqlite.JDBC
    type: com.alibaba.druid.pool.DruidDataSource
    druid:
      initial-size: 5
      min-idle: 5
      max-active: 20
      max-wait: 60000
      time-between-eviction-runs-millis: 60000
      min-evictable-idle-time-millis: 300000
      validation-query: SELECT 1
      test-while-idle: true
      test-on-borrow: false
      test-on-return: false
      pool-prepared-statements: true
      max-pool-prepared-statement-per-connection-size: 20
      connection-properties: druid.stat.mergeSql=true;druid.stat.slowSqlMillis=5000
```