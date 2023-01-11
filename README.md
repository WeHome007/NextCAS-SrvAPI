## NextHuman开放平台规范
### API/应用鉴权
1)、从NextHuman获取账户对应的accessKey、accessSecret，用于服务/应用端的访问令牌。

2)、使用JWT协议签发访问令牌：
      a)、服务端令牌角色为role.master，应用端令牌角色为role.visit；
      
      b)、签发令牌有效时间不可超过24小时;
      
      c)、需使用系统时间的当前毫秒数(timestamp)参与签发，以用于双端时间钟的同步校验；
      
      d)、如果该应用需要在运行在NextHuman所在的云渲染环境，想实现令牌参数透传，则可以考虑将业务参数也一起放入JWT进行令牌的生成，比如可以放入当前访问用户的UID，以实现己方业务的用户身份识别和不同业务逻辑处理；
      
      e)、令牌在生成规范示例如下：
      
```
public String createVisitToken(String accessKey,String accessSecret,long expiredAt){
      SecretKey secretKey = Keys.hmacShaKeyFor(accessSecret.getBytes(StandardCharsets.UTF_8));
      JwtBuilder builder = Jwts.builder();
      builder.claim("role","role.visit");
      builder.claim("timestamp",System.currentTimeMillis());
      builder.setExpiration(new Date(expiredAt));
      return accessKey + "@" + builder.signWith(secretKey).compact();
}
```
```
public String createMasterToken(String accessKey,String accessSecret,long expiredAt){
    SecretKey secretKey = Keys.hmacShaKeyFor(accessSecret.getBytes(StandardCharsets.UTF_8));
    JwtBuilder builder = Jwts.builder();
    builder.claim("role","role.master");
    builder.claim("timestamp",System.currentTimeMillis());
    builder.setExpiration(new Date(expiredAt));
    return accessKey + "@" + builder.signWith(secretKey).compact();
}
```
3)、访问令牌通过HTTP请求头accessToken进行传递即实现彼此鉴权；

### 访问控制
1)、应用端每“启动”一次应用即会触发一次鉴权，鉴权超过账号所约定的套餐即会鉴权失败，鉴权次数自然日统计和限制，隔日重置；

2)、套餐内的“建模次数”使用完毕即会出现建模失败(照片建模/结构光建模),如需更多建模次数，需做套餐升级或与我们单独约定；

3)、不同套餐有不同等级的每日免费CDN使用量，超过使用量按正常CDN计费即可(如应用运行在NextHuman云端，系统对资源包有LRU缓存机制，会比较节省流量)；


### 资源控制
1)、可以通过API加载NextHuman账号下“自用”和“通用资产”道具资产；

2)、可以通过API加载NextHuman账号下创作的“形象”和"NPC"资产，但不可



