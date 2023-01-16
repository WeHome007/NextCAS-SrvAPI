### Bundle模型对象
| 参数字段<img width=20/>  | 参数类型<img width=80/> | 是否必须   | 备注 |
|  ----   | ----  |----  | ----  |
| id | string    | 是  | 道具Id|
| bodyId  | string | 否  | 如果是附属于Avatar的道具，则需指定资产适配的身体模型 |
| name  | string | 否  | 道具名 |
| icon  | string | 否  | 道具封面图  |
| category  | string | 是  | 道具分类  |
| gender  | int32 | 是  | 道具适用性别：0(通用)、1(男)、2(女) |
| ctime  | string | 是  | 道具创建时间 |
| size  | long | 是  | 道具大小 |


