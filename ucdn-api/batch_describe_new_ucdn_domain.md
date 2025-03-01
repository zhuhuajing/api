# 批量获取加速域名配置-BatchDescribeNewUcdnDomain

批量获取加速域名配置

# Request Parameters
|Parameter name|Type|Description|Required|
|---|---|---|---|
|ProjectId|string|项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list)|No|
|Offset|int|数据偏毅力昂，默认0，非负整数|No|
|Limit|int|返回数据长度，如果制定了Offset，则默认20，否则默认全部，非负整数|No|
|DomainId.n|string|域名id，创建域名时生成的id，默认获取账号下的所有域名信息，n为自然数|No|
|ChannelType|string|渠道ufile、uvideo|No|
|ChargeStatus|int|1-待测试，2-测试中，3-测试失败，4-测试过期，5-计费中|No|
|MonthChargeType|int|30-95带宽,31-日均峰值,32-第四峰值|No|

# Response Elements
|Parameter name|Type|Description|Required|
|---|---|---|---|
|RetCode|int|返回码|**Yes**|
|Action|string|操作名称|**Yes**|
|TotalCount|int|满足条件的域名个数|No|
|MaxDomainNum|int|最大域名数量，默认20|No|
|ChargeType|string|当前计费方式，traffic代表按流量包计费，bandwidth按带宽付费，trafficused代表按流量后付费|No|
|LastChargeType|string|表示最后一次切换的计费方式，traffic代表按流量包计费，bandwidth按带宽付费，trafficused代表按流量后付费|No|
|Arrearage|bool|是否欠费，True-欠费，false-不欠费|No|
|Vip|string|vip标示，True-欠费，false-不欠费|No|
|DomainList|array||No|

## DomainInfo
|Parameter name|Type|Description|Required|
|---|---|---|---|
|OriginIp|array|源站ip即cdn服务器回源访问的ip地址。支持多个源站ip，多个源站ip，可表述为如：[1.1.1.1,2.2.2.2]|**Yes**|
|TestUrl|string|测试url，用于域名创建加速时的测试|**Yes**|
|CdnType|string|加速域名的业务类型，web代表网站，stream代表视频，download代表下载。|**Yes**|
|CacheConf|array|缓存配置规则列表|**Yes**|
|AreaCode|string|查询带宽区域 cn代表国内 abroad代表海外 不填默认为全部区域|No|
|OriginHost|string|回源Http请求头部Host，默认是加速域名|No|
|OriginPort|int|回源端口|No|
|CdnProtocol|string|加速类型http,http\|https|No|
|OriginProtocol|string|源站协议http，http\|https   默认http|No|
|CertName|string|证书名称|No|
|Tag|string|业务组，默认为Default|No|
|CacheHost|string|缓存Host，不同的域名可以配置为同一个CacheHost来实现缓存共享，默认为加速域名|No|
|ReferType|int|0白名单，1黑名单|No|
|NullRefer|bool|ReferType为白名单时，NullRefer为false代表不允许NULL refer访问，为true代表允许Null refer访问|No|
|ReferList|array|Refer列表，支持正则表达式|No|
|Domain|string|域名，用户创建加速的域名|No|
|DomainId|string|域名id，创建域名时生成的id|No|
|Status|string|创建的加速域名的当前的状态。check代表审核中，checkSuccess代表审核通过，checkFail代表审核失败，enable代表加速中，disable代表停止加速，delete代表删除加速 enableing代表正在开启加速，disableing代表正在停止加速中，deleteing代表删除中|No|
|Cname|string|cdn域名。创建加速域名生成的cdn域名，用于设置CNAME记录|No|
|CreateTime|int|域名创建的时间。格式：时间戳|No|
|ValidTime|int|开始分配Cname时间。格式：时间戳|No|
|AccessConf|object|访问控制|No|
|ReferStatus|bool|refer配置开关，true打开，false关闭|No|
|HttpsStatusCn|string|国内https状态 enableing-开启中 fail-开启失败 enable-启用 disable-未启用|No|
|HttpsStatusAbroad|string|国外https状态 enableing-开启中  fail-开启失败 enable-启用 disable-未启用|No|

## CacheConf
|Parameter name|Type|Description|Required|
|---|---|---|---|
|HttpCodePattern|string|状态码默认情况只缓存200类状态码，支持正则|No|
|PathPattern|string|路径模式，支持正则|No|
|Description|string|缓存规则描述|No|
|CacheTTL|int|缓存时间|No|
|CacheUnit|string|缓存时间的单位。sec（秒），min（分钟），hour（小时），day（天）|No|
|CacheBehavior|bool|是否缓存，true为缓存，false为不缓存。为false的情况下，CacheTTL和CacheUnit强制不生效|No|
|IgnoreQueryString|bool|是否忽略参数缓存（false为不忽略，true为忽略，默认为false）|No|
|FollowOriginRule|bool|是否优先遵循源站头部缓存策略，false为不优先遵循源站，true为优先遵循源站缓存头部。默认为false|No|

## AccessConf
|Parameter name|Type|Description|Required|
|---|---|---|---|
|IpBlacklist|string|多个ip用逗号隔开|No|

# Request Example
```
https://api.ucloud.cn/?Action=BatchDescribeNewUcdnDomain
```

# Response Example
```
{
    "Action": "BatchDescribeNewUcdnDomainResponse", 
    "RetCode": 0
}
```

