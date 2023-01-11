## JavaSDK
POM引入:
```
<dependency>
  <groupId>cn.nexthuman.open</groupId>
  <artifactId>nextsrv-java</artifactId>
  <version>1.0.5</version>
</dependency>
```
调用形式：
```
NextHumanClient client = new NextHumanClient("${accessKey}","${accessSecret}");
client.setUrl("https://dev.nexthuman.cn/open");//设置测试环境地址(线上无需调用)

//自建环境列表获取
GetLiveNusRequest req5 = new GetLiveNusRequest();
req5.setPage(1);
req5.setSize(50);
System.out.println(JSON.toJSONString(client.execute(req5),true));

//查询云渲染运行中数量
System.out.print(JSON.toJSONString(client.execute(new CountRuningInstancesRequest()),true));

//生成24小时有效的用户访问Token
System.out.println(client.createVisitToken(System.currentTimeMillis() + 24 * 60 * 60 * 1000));
```

