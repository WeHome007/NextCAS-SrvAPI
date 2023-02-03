## 服务端接口文档

### 服务请求域名

<kbd>业务请求域名：https://nexthuman.cn/open</kbd>
<br/>
<kbd>业务请求格式：application/json</kbd>

### 分类获取道具
<kbd>请求路径：/srv/bundle/getBundles</kbd>
| 参数字段<img width=20/>  | 参数类型<img width=80/>    | 是否必须<img width=20/>    | 备注 |
|  ----   | ----  |----  |----  |
| [category](category.md) |string | 是| 根据NextHuman平台道具分类获取道具列表|
| scope |string | 是| NextHuman平台道具范围：creation(用户创作)、imports(用户自用)、pri(定制)、inapp(由SDK创建),目前只允许以上几个scope的数据<br/>获取，关联资产属于NextHuman平台上的“已购买和商城”不支持SDK调用|
| page |int32 | 是| 当前分页码，从1开始 |
| pageSize |int32 | 是| 分页大小 |

<kbd>请求响应：</kbd>
| 参数字段<img width=20/>  | 参数类型<img width=80/>    | 是否必须<img width=20/>    | 备注 |
|  ----   | ----  |----  |----  |
| code | int32     | 是    | 返回接口，0表示业务请求正常，其它数值皆为异常 |
| msg  | string     | 否    | 业务错误说明 |
|errorCode | string | 否 | 业务错误码|
| data | [Page](page.md)<[Bundle](bundle.md)> | 否    | 分页结果 |


### 获取道具详情
<kbd>请求路径：/srv/bundle/getBundleById</kbd>
| 参数字段<img width=20/>  | 参数类型<img width=80/>    | 是否必须<img width=20/>    | 备注 |
|  ----   | ----  |----  |----  |
| bundleId | string | 是 | 道具Id|

<kbd>请求响应：</kbd>
| 参数字段<img width=20/>  | 参数类型<img width=80/>    | 是否必须<img width=20/>    | 备注 |
|  ----   | ----  |----  |----  |
| code | int32     | 是    | 返回接口，0表示业务请求正常，其它数值皆为异常 |
| msg  | string     | 否    | 业务错误说明 |
| errorCode | string | 否 | 业务错误码 |
| data | [Bundle](bundle.md) | 否    | 道具详情 |

### 分类获取环境
<kbd>请求路径：/srv/bundle/getNuses</kbd>
| 参数字段<img width=20/>  | 参数类型<img width=80/>    | 是否必须<img width=20/>    | 备注 |
|  ----   | ----  |----  |----  |
| [scope](scope.md) | string | 是| NextHuman平台道具范围：creation(用户创作)、imports(用户自用)、<br/>、pri(定制)，目前只允许以上几个scope的数据获取，<br/>关联资产属于NextHuman平台上的“已购买和商城”不支持SDK调用|
| page |int32 | 是| 当前分页码，从1开始 |
| pageSize |int32 | 是| 分页大小 |

<kbd>请求响应：</kbd>
| 参数字段<img width=20/>  | 参数类型<img width=80/>    | 是否必须<img width=20/>    | 备注 |
|  ----   | ----  |----  |----  |
| code | int32     | 是    | 返回接口，0表示业务请求正常，其它数值皆为异常 |
| msg  | string     | 否    | 业务错误说明 |
| errorCode | string | 否 | 业务错误码 |
| data | [Page](page.md)<[Nus](nus.md)> | 否    | 分页结果 |
