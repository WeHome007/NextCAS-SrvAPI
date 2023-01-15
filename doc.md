## 服务端接口文档

### 服务请求域名

域名：https://nexthuman.cn/open

### 分类获取道具

| 参数字段 | 参数类型 | 是否必须 | 备注 |
|  ----   | ----  |----  |----  |
| category |string | 是| 根据NextHuman平台道具分类获取道具列表|
| scope |string | 是| NextHuman平台的道具范围：creation(用户创作)、imports(用户自用)、free(通用/免费)、pri(定制)、inapp(由SDK创建)，目前只允许以上几个scope的数据获取，已购买和商城不支持SDK单独调用|
| page |int32 | 是| 当前分页码，从1开始 |
| pageSize |int32 | 是| 分页大小 |


### 获取道具详情

| 参数字段 | 参数类型 | 是否必须 | 备注 |
|  ----   | ----  |----  |----  |
| xxxx |xxx | xxx| xxx|

### 分类获取环境

| 参数字段 | 参数类型 | 是否必须 | 备注 |
|  ----   | ----  |----  |----  |
| xxxx |xxx | xxx| xxx|


### 获取环境详情

| 参数字段 | 参数类型 | 是否必须 | 备注 |
|  ----   | ----  |----  |----  |
| xxxx |xxx | xxx| xxx|
