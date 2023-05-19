## 1.1Maven

```xml
<!--mapStruct依赖 高性能对象映射-->
            <!--mapstruct核心-->
            <dependency>
                <groupId>org.mapstruct</groupId>
                <artifactId>mapstruct</artifactId>
                <version>1.5.0.Beta1</version>
            </dependency>
            <!--mapstruct编译-->
            <dependency>
                <groupId>org.mapstruct</groupId>
                <artifactId>mapstruct-processor</artifactId>
                <version>1.5.0.Beta1</version>
            </dependency>

<-- Lombok依赖：（版本最好在1.16.16以上，否则会出现问题）通常是和lombok一起使用 -->
		<dependency>
            <groupid>org.projectlombok</groupid>
            <artifactid>lombok</artifactid>
            <version>1.18.12</version> 
        </dependency>
    
    
    
    <build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.5.1</version>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
                <annotationProcessorPaths>
                    <path>
                        <groupId>org.mapstruct</groupId>
                        <artifactId>mapstruct-processor</artifactId>
                        <version>${org.mapstruct.version}</version>
                    </path>
                </annotationProcessorPaths>
            </configuration>
        </plugin>
    </plugins>
    </build>
```

下载插件(不是必须的，但是挺好用)
**idea中下载 mapstruct support 插件，安装重启Idea**







#### 例子

mapper

```java
@Mapper
public interface StudentMapper {
    StudentMapper INSTANCE = Mappers.getMapper(StudentMapper.class);
    @Mapping(source = "gender.name", target = "gender")
    @Mapping(source = "birthday", target = "birthday", dateFormat = "yyyy-MM-dd HH:mm:ss")
    StudentVO student2StudentVO(Student student);
}

调用
    StudentVO studentVO = StudentMapper.INSTANCE.student2StudentVO(student);
```



```java
@Mapper(imports = CustomProcessors.class)
public interface DepartmentsMapper {  
    @Mapping(target = "status", expression = "java( DepartmentsMapper.toStatus(department.getStatus()) )")
    DepartmentsVO boToVo(DepartmentBO department);
    static String toStatus(String status){
        return status + "状态";
    }
}
```

多对象转一个对象

```Java
@Mapping(source = "student.gender.name", target = "gender")
    @Mapping(source = "student.birthday", target = "birthday", dateFormat = "yyyy-MM-dd HH:mm:ss")
    @Mapping(source = "course.courseName", target = "course")
    StudentVO studentAndCourse2StudentVO(Student student, Course course);
```

默认值

```java
@Mapping(source = "student.gender.name", target = "gender")
    @Mapping(source = "student.birthday", target = "birthday", dateFormat = "yyyy-MM-dd HH:mm:ss")
    @Mapping(source = "course.courseName", target = "course")
    @Mapping(target = "name", source = "student.name", defaultValue = "张三")
    StudentVO studentAndCourse2StudentVO(Student student, Course course);
```



#### 转日期

```java
@Mapping(source = "birthday", target = "birthday", dateFormat = "yyyy-MM-dd HH:mm:ss")
    StudentVO student2StudentVO(Student student);
```

