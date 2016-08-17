## 1. 接口描述 
本接口(ModifyRedisProject)用于修改CRS实例所属项目。
接口请求域名：<font style='color:red'>redis.api.qcloud.com </font>

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href='/doc/api/260/1753' title='公共请求参数'>公共请求参数</a>页面。其中，此接口的Action字段为ModifyRedisProject。

| 参数名称 | 是否必选 | 类型 | 描述 |
|---------|---------|---------|
| redisIds.n | 是 | String | 可通过[DescribeRedis](http://www.qcloud.com/doc/api/260/1384)接口查询实例列表|
| projectId | 是 | UInt | 项目ID,取值以用户账户>用户账户相关接口查询>[项目列表](https://www.qcloud.com/doc/api/403/4400)返回的projectId为准|

## 3. 输出参数
<table class="t"><tbody><tr>
<th><b>参数名称</b></th>
<th><b>类型</b></th>
<th><b>描述</b></th>
<tr>
<td> code <td> Int <td> 公共错误码，0表示成功，其他值表示失败。详见错误码页面的<a href='https://www.qcloud.com/doc/api/372/%E9%94%99%E8%AF%AF%E7%A0%81#1.E3.80.81.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81' title='公共错误码'>公共错误码</a>。
<tr>
<td> message <td> String <td> 错误信息
</tbody></table>

## 4. 示例
```
  https://redis.api.qcloud.com/v2/index.php?Action=ModifyRedisProject
	&<公共请求参数>
	&redisIds.0=crs-ifmymj41
	&projectId=1004306
```
返回示例如下：
```
{
    "code": 0,
    "message": ""
}
```

