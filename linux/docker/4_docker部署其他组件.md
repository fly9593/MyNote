# 安装mysql
docker pull mysql

```
docker run -p 3306:3306 --name mysql-master -v /mydata/mysql/master/log:/var/log/mysql -v /mydata/mysql/master/data:/var/lib/mysql -v /mydata/mysql/master/conf:/etc/mysql -e MYSQL_ROOT_PASSWORD=root -d mysql:5.7

docker run -p 3306:3306 --name mysql-master -v /mydata/mysql/master/log:/var/log/mysql -v /mydata/mysql/master/data:/var/lib/mysql -v /mydata/mysql/master/conf:/etc/mysql/conf.d  -v /mydata/mysql/mysql-files:/var/lib/mysql-files -e MYSQL_ROOT_PASSWORD=root -d mysql:8.0
```


# 部署tomcat8
## 下载镜像
```
docker pull tomcat:8.0

```

## 部署镜像
```
docker run -d -p 8080:8080 --name tomcatqaq tomcat:8.0
```

## 如果8080端口被占用：
```
docker run -d -p 8090:8080 --name tomcatqaq tomcat:8.0
```

## 进入正在运行的tomcat9.0容器
```
docker exec -it tomcatqaq /bin/bash
```

## 查看tomcat的Java版本
java -version


## 部署springboot项目
```
docker cp test_springboot-0.0.1-SNAPSHOT.war tomcatqaq:/usr/local/tomcat/webapps/
```

# 部署tomcat9
## 下载镜像
```
docker pull tomcat:9.0
```

## 部署镜像
```
docker run -d -p 9090:8080 --name myTomcat9 tomcat:9.0
```

## 进入正在运行的tomcat9.0容器
```
docker exec -it myTomcat9 /bin/bash
```

## 部署springboot项目
```
docker cp test_springboot-0.0.1-SNAPSHOT.war myTomcat9:/usr/local/tomcat/webapps/
```

## 常用命令
```
docker exec -it myTomcat9 /bin/bash
ls
ls webapps
ls webapps.dist

ls /usr/local/tomcat/logs
cat /usr/local/tomcat/logs/catalina.2024-08-06.log

chmod -R 755 /usr/local/tomcat/webapps/
```