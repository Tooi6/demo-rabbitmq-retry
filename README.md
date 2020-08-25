### RabbitMQ可靠性投递——消息落库

#### 介绍博客
https://www.jianshu.com/p/773fe1a082e3

#### 测试

- 启动项目（运行DemoRabbitmqRetryApplication）

- 运行测试 testCreateOrder() 创建订单

```java
@SpringBootTest
class DemoRabbitmqRetryApplicationTests {

    @Autowired
    private RabbitOrderSender rabbitOrderSender;

    @Autowired
    private OrderService orderService;

    @Test
    public void testCreateOrder() throws Exception {
        Order order = new Order();
        order.setId("2020082400002");
        order.setName("测试创建订单");
        order.setMessageId(System.currentTimeMillis() + "$" + UUID.randomUUID().toString());
        orderService.createOrder(order);
    }

}
```