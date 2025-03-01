# 查询主备Redis-DescribeURedisGroup

查询主备Redis

# Request Parameters
|Parameter name|Type|Description|Required|
|---|---|---|---|
|Region|string|地域。 参见 [地域和可用区列表](api/summary/regionlist)|**Yes**|
|ProjectId|string|项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list)|No|
|GroupId|string|组的ID,如果指定则获取描述，否则为列表操 作,需指定Offset/Limit|No|
|Offset|int|分页显示的起始偏移, 默认值为0|No|
|Limit|int|分页显示的条目数, 默认值为20|No|

# Response Elements
|Parameter name|Type|Description|Required|
|---|---|---|---|
|RetCode|int|返回码|**Yes**|
|Action|string|操作名称|**Yes**|
|TotalCount|int|组的总的节点个数|No|
|DataSet|array|组列表 参见 URedisGroupSet|No|

## URedisGroupSet
|Parameter name|Type|Description|Required|
|---|---|---|---|
|Zone|string|实例所在可用区，或者master redis所在可用区，参见 [可用区列表](api/summary/regionlist)|No|
|VPCId|string||**Yes**|
|RewriteTime|int|返回运维时间 0 //0点 1 //1点 以此类推|**Yes**|
|Role|string|实例类型|**Yes**|
|GroupId|string|组ID|No|
|Name|string|组名称|No|
|Type|string||No|
|SubnetId|string||No|
|Protocol|string|协议|No|
|MemorySize|int|容量单位GB|No|
|GroupName|string|组名称|No|
|ConfigId|string|节点的配置ID|No|
|VirtualIP|string|节点的虚拟IP地址|No|
|Port|int|节点分配的服务端口|No|
|Size|int|容量单位GB|No|
|UsedSize|int|使用量单位MB|No|
|AutoBackup|string|是否需要自动备份,enable,disable|No|
|BackupTime|int|组自动备份开始时间,单位小时计,范围[0-23]|No|
|HighAvailability|string|是否开启高可用,enable,disable|No|
|Version|string|Redis版本信息|No|
|ExpireTime|int|过期时间 (UNIX时间戳)|No|
|ChargeType|string|计费类型:Year,Month,Dynamic 默认Dynamic|No|
|State|string|状态标记 Creating // 初始化中 CreateFail // 创建失败 Deleting // 删除中 DeleteFail // 删除失败 Running // 运行 Resizing // 容量调整中 ResizeFail // 容量调整失败 Configing // 配置中 ConfigFail // 配置失败|No|
|CreateTime|int|创建时间 (UNIX时间戳)|No|
|ModifyTime|int|修改时间 (UNIX时间戳)|No|
|Tag|string|业务组名称|No|
|SlaveZone|string|跨机房URedis，slave redis所在可用区，参见 [可用区列表](api/summary/regionlist)|No|

# Request Example
```
https://api.ucloud.cn/?Action=DescribeURedisGroup
&Region=cn-east-01
&Offset=0
&Limit=20
```

# Response Example
```
{
    "Action": "DescribeURedisGroupResponse", 
    "TotalCount": 2, 
    "RetCode": 0, 
    "DataSet": [
        {
            "DisasterRecover": "enable", 
            "Version": 3, 
            "Name": "test1", 
            "BackupTime": 14, 
            "Port": 3306, 
            "UsedSize": 104, 
            "VirtualIP": "10.4.4.11", 
            "ExpireTime": 1403549482, 
            "State": "Running", 
            "Tag": "Default", 
            "AutoBackup": "enable", 
            "ChargeType": "Year", 
            "ModifyTime": 1403249482, 
            "ConfigId": "24149c99-4df6-4b5a-99b4-8ab1ca2d7bbb", 
            "GroupId": "uredis-0vcq2a", 
            "CreateTime": 1403249482, 
            "Size": 1024
        }, 
        {
            "DisasterRecover": "enable", 
            "Version": 3, 
            "Name": "testr", 
            "BackupTime": 14, 
            "Port": 3302, 
            "UsedSize": 10, 
            "VirtualIP": "10.4.4.12", 
            "ExpireTime": 1403549482, 
            "State": "Running", 
            "Tag": "Default", 
            "AutoBackup": "enable", 
            "ChargeType": "Year", 
            "ModifyTime": 1403249482, 
            "ConfigId": "24149c99-4df6-4b5a-99b4-8ab1ca2d7bbr", 
            "GroupId": "uredis-0vcq2r", 
            "CreateTime": 1403249482, 
            "Size": 1024
        }
    ]
}
```

