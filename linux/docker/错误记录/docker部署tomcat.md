# test_springboot-0.0.1-SNAPSHOT.jar中没有主清单属性
错误原因：springboot项目中未配置spring-boot-maven-plugin插件或改插件被禁用
解决方法：maven中添加如下配置：
```
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <version>${spring-boot.version}</version>
                <configuration>
                    <mainClass>com.example.test_springboot.TestSpringbootApplication</mainClass>
                   <!-- <skip>true</skip> -->
                </configuration>
                <executions>
                    <execution>
                        <id>repackage</id>
                        <goals>
                            <goal>repackage</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
```

