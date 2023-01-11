## NextHuman开放平台规范
### API/应用鉴权
#### 1)、从NextHuman获取账户对应的accessKey、accessSecret，用于服务/应用端的访问令牌。
#### 2)、使用JWT协议签发访问令牌，服务端令牌角色为role.master，应用端令牌角色为role.visit，生成规范示例如下：
```
public String createVisitToken(String accessKey,String accessSecret,long expiredAt){
      SecretKey secretKey = Keys.hmacShaKeyFor(accessSecret.getBytes(StandardCharsets.UTF_8));
      JwtBuilder builder = Jwts.builder();
      builder.claim("role",WebArgumentResolver.role_visit);
      builder.claim("timestamp",System.currentTimeMillis());
      builder.setExpiration(new Date(expiredAt));
      return accessKey + "@" + builder.signWith(secretKey).compact();
}
public String createMasterToken(String accessKey,String accessSecret,long expiredAt){
    SecretKey secretKey = Keys.hmacShaKeyFor(accessSecret.getBytes(StandardCharsets.UTF_8));
    JwtBuilder builder = Jwts.builder();
    builder.claim("role",WebArgumentResolver.role_master);
    builder.claim("timestamp",System.currentTimeMillis());
    builder.setExpiration(new Date(expiredAt));
    return accessKey + "@" + builder.signWith(secretKey).compact();
}
```
#### 3)、访问令牌通过HTTP请求头accessToken进行传递即实现彼此鉴权；


