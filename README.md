# 安装说明

### 安装环境准备

- 安装 JDK 1.8 以上
- 安装 MySql 5.7 以上
- 安装 Tomcat 7.0 以上

### 安装步骤

1. 建立数据库
2. 拷贝powerteam-0.0.1.war到tomcat的webapps目录下
3. 启动tomcat

### 建立PowerTeam数据库

1. 打开Mysql管理工具(推荐使用 MySQL Workbench)
2. 执行db.sql脚本
3. **可选操作** 执行demo_data.sql演示数据脚本

### 安装PowerTeam

1. 拷贝powerteam-0.0.1.war到tomcat的webapps目录下
2. 找到 tomcat安装目录\webapps\powerteam\WEB-INF\classes\application-powerteam.yml 配置文件
3. 修改datasource.url 中的ip地址和端口和数据库名称(端口默认是**3306**，数据库默认是**powerteam**)
4. 修改datasource.username 数据库用户名
5. 修改datasource.password 数据库密码
6. 启动tomcat

### 运行PowerTeam
访问 http://localhost:8080/powerteam enjoy it! 如果任何问题，请加入QQ群(466234012)咨询
> 默认的管理员帐号为admin 密码为admin

### 常见部署问题

1. **tomcat和mysql不在同一台服务器上**

> 请保证mysql服务器的防火墙已开放3306端口(默认端口，如果是其他端口请举一反三)
> 请保证连接mysql的用户名具有外网访问的权限,如果没有请联系mysql管理员授权用户名具备tomcat服务器访问mysql服务器的权限

2. **tomcat绑定80端口**

> 找到 tomcat\conf\server.xml 修改port="80" 重启tomcat

```
<Connector port="8080" protocol="HTTP/1.1"  connectionTimeout="20000" redirectPort="8443" />
```

3. **访问路径去掉/powerteam 采用http://localhost:8080访问**

> 找到 tomcat\conf\server.xml 在Host节中加入该行 重启tomcat

```
<Context path="/" docBase="powerteam" reloadable="true"/>
```
修改后

```
<Host name="localhost"  appBase="webapps" unpackWARs="true" autoDeploy="true">
    ...
    <Context path="/" docBase="powerteam" reloadable="true"/>
    ...
</Host>
```