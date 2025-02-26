开发包（com.pandj）
现阶段版本：
- 1.0.0.RELEASE

以包含一下jar包
- 无需引用：Gson
- 需引用，无需指定版本
```xml
<springdoc.version>1.7.0</springdoc.version>
<develop-plus-bom.version>1.0.0-SNAPSHOT</develop-plus-bom.version>
<pingyin4j.version>2.5.1</pingyin4j.version>
<xstream.version>1.4.21</xstream.version>
<xxl-job.version>2.4.2</xxl-job.version>
<fastexcel.version>1.0.0</fastexcel.version>
<grpc-boot.version>3.1.0.RELEASE</grpc-boot.version>

<!--fastexcel-->
<dependency>
    <groupId>cn.idev.excel</groupId>
    <artifactId>fastexcel</artifactId>
</dependency>

<!--grpc(service - client)-->
<dependency>
    <groupId>net.devh</groupId>
    <artifactId>grpc-spring-boot-starter</artifactId>
</dependency>

```
# 1. 使用
```xml
 <properties>
    <spring-boot.version>3.2.4</spring-boot.version>
    <spring-cloud.version>2023.0.1</spring-cloud.version>
    <spring-cloud-alibaba.version>2023.0.1.0</spring-cloud-alibaba.version>
    <mybatis-plus.version>3.5.9</mybatis-plus.version>
    <develop-plus-bom.version>1.0.0-SNAPSHOT</develop-plus-bom.version>
</properties>

<dependencies>
    <dependency>
      <groupId>com.pandj</groupId>
      <artifactId>develop-plus-选择对应的模块</artifactId>
    </dependency>
    
    <!--swagger-->
    <dependency>
      <groupId>org.springdoc</groupId>
      <artifactId>springdoc-openapi-webmvc-core</artifactId>
    </dependency>
</dependencies>

<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.pandj</groupId>
            <artifactId>develop-plus-bom</artifactId>
            <version>${develop-plus-bom.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-bom</artifactId>
            <version>${mybatis-plus.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-dependencies</artifactId>
            <version>${spring-boot.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-dependencies</artifactId>
            <version>${spring-cloud.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-alibaba-dependencies</artifactId>
            <version>${spring-cloud-alibaba.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```
- 其他引入规则
  - nacos
  ```xml
  <dependency>
      <groupId>com.alibaba.cloud</groupId>
      <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
  </dependency>
  <dependency>
      <groupId>com.alibaba.cloud</groupId>
      <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
  </dependency>
  <!--配置发现 2020.1.x之后需要手动添加 -->
  <dependency>
      <groupId>org.springframework.cloud</groupId>
      <artifactId>spring-cloud-starter-bootstrap</artifactId>
  </dependency>
  <!--解决网关lb的问题-->
  <dependency>
      <groupId>org.springframework.cloud</groupId>
      <artifactId>spring-cloud-starter-loadbalancer</artifactId>
  </dependency>
  ```
  
  - mybatis-plus
  ```xml
  <dependency>
      <groupId>com.mysql</groupId>
      <artifactId>mysql-connector-j</artifactId>
      <scope>runtime</scope>
  </dependency>
  <!--mybatis-plus-->
  <dependency>
      <groupId>com.baomidou</groupId>
      <artifactId>mybatis-plus-spring-boot3-starter</artifactId>
  </dependency>
  <!-- jdk 11+ 引入可选模块 -->
  <dependency>
      <groupId>com.baomidou</groupId>
      <artifactId>mybatis-plus-jsqlparser</artifactId>
  </dependency>
  <!--代码生成器-->
  <dependency>
      <groupId>com.baomidou</groupId>
      <artifactId>mybatis-plus-generator</artifactId>
  </dependency>
  <!--模版-->
  <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-freemarker</artifactId>
  </dependency>
  ```
  
  - springboot相关
  ```xml
  <!--参数校验-->
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
  </dependency>
  <!--redis-->
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-redis</artifactId>
  </dependency>
  <!--Email工具-->
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-mail</artifactId>
  </dependency>
  ```
  
  - springcloud相关
  ```xml
  <!-- Feign -->
  <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
  </dependency>
  ```


# 2. 配置中心
nacos
```yaml
spring:
  cloud:
    nacos:
      config:
        server-addr: pandj.com
        namespace: xxxxxxxxxxxxx
        group: DEFAULT_GROUP
        file-extension: yaml
        username: xxxx
        password: xxxxxx
      discovery:
        server-addr: ${spring.cloud.nacos.config.server-addr}
        namespace: ${spring.cloud.nacos.config.namespace}
        group: ${spring.cloud.nacos.config.group}
        username: ${spring.cloud.nacos.config.username}
        password: ${spring.cloud.nacos.config.password}
```