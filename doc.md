## 服务端接口文档

### 服务请求域名

<kbd>业务域名：https://nexthuman.cn/open</kbd>

### 分类获取道具:<kbd>/srv/bundle/getBundles</kbd>

| 参数字段 | 参数类型     | 是否必须    | 备注 |
|  ----   | ----  |----  |----  |
| category |string | 是| 根据NextHuman平台道具分类获取道具列表|
| scope |string | 是| NextHuman平台道具范围：creation(用户创作)、imports(用户自用)、free(通用/免费)、<br/>pri(定制)、inapp(由SDK创建),目前只允许以上几个scope的数据获取，已购买和商城不支持SDK单独调用|
| page |int32 | 是| 当前分页码，从1开始 |
| pageSize |int32 | 是| 分页大小 |


### 获取道具详情:<kbd>/srv/bundle/getBundleById</kbd>

| 参数字段 | 参数类型 | 是否必须 | 备注 |
|  ----   | ----  |----  |----  |
| bundleId | string | 是 | 道具Id|

### 分类获取环境:<kbd>/srv/bundle/getNuses</kbd>

| 参数字段 | 参数类型 | 是否必须 | 备注 |
|  ----   | ----  |----  |----  |
| scope | string | 是| NextHuman平台道具范围：creation(用户创作)、imports(用户自用)、free(通用/免费)、pri(定制)，<br/>目前只允许以上几个scope的数据获取，已购买和商城不支持SDK单独调用|

### 获取环境详情:<kbd>/srv/bundle/getNusById</kbd>

| 参数字段 | 参数类型 | 是否必须 | 备注 |
|  ----   | ----  |----  |----  |
| nusId |string | 是| 环境Id |

