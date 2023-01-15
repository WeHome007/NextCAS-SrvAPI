## 服务端接口文档

### 服务请求域名

<kbd>业务域名：https://nexthuman.cn/open</kbd>

### 分类获取道具:<kbd>/srv/bundle/getBundles</kbd>
<kbd>Request</kbd>
| <div style="width: 80px">参数字段</div> | <div style="width: 150px;">参数类型</div>     | <div style="width: 80px">是否必须</div>    | 备注 |
|  ----   | ----  |----  |----  |
| category |string | 是| 根据NextHuman平台道具分类获取道具列表|
| scope |string | 是| NextHuman平台道具范围：creation(用户创作)、imports(用户自用)、free(通用/免费)、<br/>pri(定制)、inapp(由SDK创建),目前只允许以上几个scope的数据获取，已购买和商城<br/>不支持SDK单独调用|
| page |int32 | 是| 当前分页码，从1开始 |
| pageSize |int32 | 是| 分页大小 |

<kbd>Response</kbd>
| <div style="width: 80px">参数字段</div> | <div style="width: 150px;">参数类型</div>     | <div style="width: 80px">是否必须</div>    | 备注 |
|  ----   | ----  |----  |----  |
| code | int32     | 是    | 返回接口，0表示业务请求正常，其它数值皆为异常 |
| msg  | string     | 否    | 业务错误说明 |
|errorCode | string | 否 | 业务错误码|
| data | [Page](page.md)<[Bundle](bundle.md)> | 否    | 分页结果 |



### 获取道具详情:<kbd>/srv/bundle/getBundleById</kbd>
<kbd>Request</kbd>
| <div style="width: 80px">参数字段</div> | <div style="width: 150px;">参数类型</div>     | <div style="width: 80px">是否必须</div>    | 备注 |
|  ----   | ----  |----  |----  |
| bundleId | string | 是 | 道具Id|

<kbd>Response</kbd>
| <div style="width: 80px">参数字段</div> | <div style="width: 150px;">参数类型</div>     | <div style="width: 80px">是否必须</div>    | 备注 |
|  ----   | ----  |----  |----  |
| code | int32     | 是    | 返回接口，0表示业务请求正常，其它数值皆为异常 |
| msg  | string     | 否    | 业务错误说明 |
| errorCode | string | 否 | 业务错误码 |
| data | [Bundle](bundle.md) | 否    | 道具详情 |

### 分类获取环境:<kbd>/srv/bundle/getNuses</kbd>
<kbd>Request</kbd>
| 参数字段 | 参数类型 | 是否必须 | 备注 |
|  ----   | ----  |----  |----  |
| scope | string | 是| NextHuman平台道具范围：creation(用户创作)、imports(用户自用)、free(通用/免费)、<br/>pri(定制)，目前只允许以上几个scope的数据获取，已购买和商城<br/>不支持SDK单独调用|

<kbd>Response</kbd>
| 参数字段 | 参数类型     | 是否必须    | 备注 |
|  ----   | ----  |----  |----  |
| code | int32     | 是    | 返回接口，0表示业务请求正常，其它数值皆为异常 |
| msg  | string     | 否    | 业务错误说明 |
| errorCode | string | 否 | 业务错误码 |
| data | [Page](page.md)<[Nus](nus.md)> | 否    | 分页结果 |
