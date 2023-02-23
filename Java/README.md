## JavaSDK
POM引入:
```
<dependency>
  <groupId>cn.nexthuman.open</groupId>
  <artifactId>nextsrv-java</artifactId>
  <version>1.0.7</version>
</dependency>
```
SDK初始化：
```
NextHumanClient client = new NextHumanClient("${accessKey}","${accessSecret}");
```
令牌生成
```
//生成24小时有效的“用户”访问Token
String visitToken = client.createVisitToken(System.currentTimeMillis() + 24 * 60 * 60 * 1000);
//生成24小时有效的"服务端"访问Token
String masterToken = client.createMasterToken(System.currentTimeMillis() + 24 * 60 * 60 * 1000);
```
分类获取道具
```
GetBundlesRequest request = new GetBundlesRequest();
request.setPage(1);
request.setSize(50);
request.setScope("free");
request.setCategory("shoes");
GetBundlesReponse response = (GetBundlesReponse)client.execute(request);
```
获取道具详情
```
GetBundleByIdRequest request = new GetBundleByIdRequest();
request.setBundleId("shoes_62fe071fc796115aac8a6c2d");
GetBundleByIdResponse response = (GetBundleByIdResponse)client.execute(request);
```
分类获取环境
```
GetNusesRequest request = new GetNusesRequest();
request.setPage(1);
request.setSize(50);
request.setScope("free");
GetNusesResponse response = (GetNusesResponse)client.execute(request);
```


