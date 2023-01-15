## NextHuman开放平台
### 接口文档

[接口文档](doc.md)


### 应用鉴权
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
1)、应用端每“启动”一次应用即会触发一次鉴权，鉴权超过账号所约定的套餐即会鉴权失败，鉴权次数按自然日统计和限制，隔日重置；

2)、套餐内的“建模次数”使用完毕即会出现建模失败(照片建模/结构光建模),如需更多建模次数，需做套餐升级或与我们单独约定；

3)、不同套餐有不同等级的每日免费CDN使用量，超过使用量按正常CDN计费即可(如应用运行在NextHuman云端，系统对资源包有LRU缓存机制会比较节省流量，如运行在用户端则在用户会有对应的LRU缓存机制)；

4)、其他按量使用的相关资源参见官方说明；


### 资源控制
1)、可以通过API加载NextHuman账号下“自用”和“通用资产”道具资产,在己方应用中可以自己买卖账号下“自用资产”(己方业务逻辑)，可以在己方应用中将“NextHuman资产”作为免费道具给用户使用，但不可在己方应用售卖NextHuman平台的“通用资产”给己方用户；

2)、可以通过API加载NextHuman账号下创作的“形象”、"NPC"、“环境”资产，但不可使用API编辑这类由NextHuman客户端创作的这类资产；

3)、通过API创建的“形象”资产，API可以随意编辑和删除(软删除，避免用户引用出错)；

4)、特别注意的是：不可在己方应用中使用在NextHuman商城中购买的资产(不可在应用中二次分发)，也不可单独接口加载NextHuman商城中已购的资产(除上述第2条这类特殊情况)；



