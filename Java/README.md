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

角色复制
```
CopyAvatarRequest request = new CopyAvatarRequest();
request.setName("副本001");
request.setSrcAvatarId("${avatarId}");
request.setDressups(null);//如果设置了装扮道具，则以该装扮作为新角色的装扮
CopyAvatarResponse response = (CopyAvatarResponse)client.execute(request);
```

角色更新
```
UpdateAvatarRequest request = new UpdateAvatarRequest();
request.setAvatarId("${avatarId}");
request.setDressups(dressups);
request.setMakeups(makeups);
request.setName("成吉思汗");
request.setIcon(icon);
BaseResponse response = client.execute(request);
```


