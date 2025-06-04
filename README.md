<h1 align="center">develop-plus-bom</h1>

> 开发工具集合BOM

## 使用说明
```xml
<properties>
    <java.version>17</java.version>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
    <!--主要BOM-->
    <mybatis-plus.version>3.5.9</mybatis-plus.version>
    <spring-boot.version>3.2.4</spring-boot.version>
    <spring-cloud.version>2023.0.1</spring-cloud.version>
    <spring-cloud-alibaba.version>2023.0.1.0</spring-cloud-alibaba.version>
    <develop-plus-bom.version>1.0.1.RELEASE</develop-plus-bom.version>
</properties>

<dependencies>
    <!-- develop-plus-bom 根据需要引入内置模块 -->
</dependencies>

<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>io.github.pandujun</groupId>
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

## 内置jar版本
- 内部jar：
  - develop-plus-core
    - 内置
      - gson
      - slf4j-api
  - develop-plus-web
    - 内置
      - develop-plus-core
      - springdoc-openapi-webmvc-core
      - spring-boot-starter-web
      - spring-boot-starter-test
  - develop-plus-feign
    - 内置
      - develop-plus-core
      - tomcat-embed-core
      - spring-cloud-starter-openfeign
      - spring-boot-starter-validation
- 外部jar：
  - pinyin4j
  - xstream
  - easyexcel
  - grpc-spring-boot-starter