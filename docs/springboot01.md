# Springboot笔记



```java
import org.springframework.boot.*; import org.springframework.boot.autoconfigure.*; import org.springframework.web.bind.annotation.*;

@RestController //Controller
@EnableAutoConfiguration //自动
public class Example {

@RequestMapping("/") //route
String home() { return "Hello World!"; }

public static void main(String[] args) { 
SpringApplication.run(Example.class, args); 
}

}
```

```java
 <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>

            </plugin>

        </plugins>
    </build>
```

打包

```
mvn package
```

打包完后，在target文件下面会生成jar包

查看jar包内容

```
jar tvf target/myproject-0.0.1-SNAPSHOT.jar
```

启动jar包

```
java -jar target/myproject-0.0.1-SNAPSHOT.jar
```



git项目地址

