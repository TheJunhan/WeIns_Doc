# Week2

## 07-13

### 评论界面的细节

- 点开评论按钮，上面是一个发表评论的组件，下面则是显示评论的组件

- 查看评论，如果有较多的评论（>8）则可以展开更多评论，更多评论则跳转到一个新的界面，显示若干条评论；如果某一条评论下面还有评论，则展示一个展开按钮（条），展开后则是平铺的评论（若有回复直接@）

## 07-14

- 单元测试：后端junit5,前端vue-jest. etc

## 07-15

- vue图形化界面的入口：命令行输入

> vue ui

### 后端

- 报错：bind not found原因:依赖注入的是接口而不是实现

- service层单元测试要注意测试类继承WeinsApplicationTests类

- 单元测试要在类前面加

```java
@RunWith(SpringRunner.class)
@SpringBootTest
```

其中SpringRunner.class是jUnit4的类

- 最好在测试类里面写上测试前后的输出便于debug

```java
@BeforeEach
public void start() {
    System.out.println("test start");
}

@AfterEach
public void end() {
    System.out.println("test end");
}
```

- 测试的时候可以设置断言，从而摆脱手动核对，常用的有

```java
import static org.junit.Assert.assertEquals;
import static org.junit.Assert.assertNull;
```

其中assertEquals的两个参数分别为期望值（expected）和实际值（actual），两者类型保持一致，expected貌似只能用String类型的，也就是说都要转化成String再进行断言比较

## 07-16

### 管理员权限分级规定

- banned(原来权限-8)
- 普通用户(0)
- 封/解禁普通用户(4) (对应二进制：100)
- 删帖子(2) (对应二进制：010)
- 删评论(1) (对应二进制：001)
- 最高管理员(8): "老板"，只有老板才能封禁/解禁管理员，或者赋予/收回任何人管理员级别的权限，老板只有一个

## 07-17
