## JavaSDK
a)、POM引入:
```
<dependency>
  <groupId>cn.nexthuman.open</groupId>
  <artifactId>nextsrv-java</artifactId>
  <version>1.0.5</version>
</dependency>
```
b)、SDK初始化：
```
NextHumanClient client = new NextHumanClient("${accessKey}","${accessSecret}");
client.setUrl("https://dev.nexthuman.cn/open");//设置测试环境地址(线上无需调用)
```
c)、令牌生成
```
//生成24小时有效的用户访问Token
System.out.println(client.createVisitToken(System.currentTimeMillis() + 24 * 60 * 60 * 1000));
```



