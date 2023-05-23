### 常用Stream流操作

##### 1.1一对一转换

```java
List<String> ids = Arrays.asList("1","2","3","4","5");
// Using stream operations
List<User> results = ids.stream()
    				.map(id -> {
                        User user = new User(Integer.valueOf(id));
                        return user;
                    })
    				.collect(Collectors.toList());
```

##### 1.2一对多转换

```java
List<String> sentences = Arrays.asList("hello world", "jia Gou");
List<String> results = sentences.stream()
    			.flatMap(sentence - > Arrays.stream(sentence.split(" ")))
    			.collect(Collectors.toList());
```

##### 1.3流操作

```java
List<String> ids = Arrays.asList("205","404","200","505","500");
List<User> results = ids.stream()
    		.filter(s -> s.length() > 2)
    		.distinct()
    		.map(Integer::valueOf)
    		.sorted(Comparator.comparingInt(o -> o))
    		.limit(3)
    		.map(id -> new User(id))
    		.collect(Collectors.toList());
```

##### 1.4生成集合

```java
ids.stream()
    .filter(detp -> dept.getId()>5)
    .collect(Collectors.toList());
.collect(Collectors.toSet())
.collect(Colletcors.toMap(User::getId , dept -> dept));
//生成拼接字符串
.collect(Collectors.joining(","));

```

##### lambda表达式进行分组

```Java
.collect(Collectors.groupingBy(fruit -> fruit.length()));
```

##### 函数式接口的实现

```java
MyInterface myObject = input -> System.out.println(input)
```

##### lambda表达式进行线程创建

```java
//        Thread thread = new Thread(new Runnable() {
//            public void run() {
//                System.out.println("Thread is running.");
//            }
//        });

Thread thread = new Thread(() -> System.out.println("Thread is running"))j;
thread.start();
```

