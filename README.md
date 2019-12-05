# kai的公共仓库
_仓库为公开项目，上传的jar包中一定不能带有密码或核心业务相关的内容_

## 如何使用
### 1. 添加仓库地址
在pom.xml中添加仓库地址
```xml
<repositories>
    <repository>
        <id>lib-repo</id>
        <url>https://raw.githubusercontent.com/Xiaotian0617/kai-repo/master/library</url>
    </repository>
</repositories>
```

### 2. 添加项目依赖
- `coin-api` 数字coin api
```xml
<dependency>
    <groupId>com.al.bcoin</groupId>
    <artifactId>coinapi</artifactId>
    <version>0.1</version>
</dependency>
```

- `influxdb-ext` influxdb扩展库，包括line protocal序列化工具和部分内置bean. 使用说明查看<influxdb-ext.md>
```xml
<dependency>
    <groupId>com.al.dbspider</groupId>
    <artifactId>influxdb-ext</artifactId>
    <version>0.1</version>
</dependency>
```
- `exchange-api` 交易所网站rest api集合
```xml
<dependency>
    <groupId>com.al.dbspider</groupId>
    <artifactId>exchange-api</artifactId>
    <version>0.1</version>
</dependency>
```

- `notice-clinet` 提醒服务客户端
```xml
<dependency>
    <groupId>com.ailu.paas</groupId>
    <artifactId>notice-client</artifactId>
    <version>3.0-RELEASE</version>
</dependency>
```

- `okex-api-v3` Okex v3接口API
```xml
<dependency>
    <groupId>com.okcoin.okex</groupId>
    <artifactId>java-sdk-api</artifactId>
    <version>1.0.0</version>
</dependency>
```

-`exchange-api` 各个交易所的API抓取 都需引入的包
```xml
    <dependency>
        <groupId>org.knowm.xchange</groupId>
        <artifactId>xchange-core</artifactId>
        <version>4.3.4-SNAPSHOT</version>
    </dependency>
```

- `bitmex-api` Bitmex接口API
```xml
<dependency>
    <groupId>org.knowm.xchange</groupId>
    <artifactId>xchange-bitmex</artifactId>
    <version>4.3.4-SNAPSHOT</version>
</dependency>
```

## 如何上传
使用deploy部署项目到本地，再通过git上传到仓库即可
1. git clone本仓库到本地, 生成本地目录
2. 在自己的库项目下使用maven部署命令，将参数修改为本地目录  
   `mvn deploy -DaltDeploymentRepository=kai-repo::default::file:<本地目录>/library`  
   在idea或者eclipse里进行命令时无需加mvn参数
   `deploy -DaltDeploymentRepository=kai-repo::default::file:<本地目录>/library`
3. git提交本地目录下文件并push到服务器
4. 修改README.md文档，或在根目录新建文档说明库的使用方法和依赖

## 问题
- pom中添加的仓库地址无效  
  如果在maven的`settings.xml`中配置有镜像，且`mirrorOf`为`*`。需要修改为`*,!kai-repo`，排除对本仓库使用镜像
