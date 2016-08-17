## 1. 接口描述
本接口(ModfiyRedisPassword)用于修改CRS实例密码。
接口请求域名：<font style='color:red'>redis.api.qcloud.com </font>

密码规则： 长度为8-16个字符；至少包含字母、数字和字符（!@#%^()）中的两种

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href='/doc/api/260/1753' title='公共请求参数'>公共请求参数</a>页面。其中，此接口的Action字段为DescribeRedis。
<table class="t"><tbody><tr>
<th><b>参数名称</b></th>
<th><b>是否必选</b></th>
<th><b>类型</b></th>
<th><b>描述</b></th>
<tr>
<td> redisId <td> 是 <td> String <td> 实例ID
<tr>
<td> oldPassword <td> 是 <td> String <td> 老密码
<tr>
<td> password <td> 是 <td> String <td> 新密码，密码规则： 长度为8-16个字符；至少包含字母、数字和字符（!@#%^()）中的两种
</tbody></table>

## 3. 输出参数
<table class="t"><tbody><tr>
<th><b>参数名称</b></th>
<th><b>类型</b></th>
<th><b>描述</b></th>
<tr>
<td> code <td> Int <td> 公共错误码, 0表示成功，其他值表示失败。详见错误码页面的<a href='https://www.qcloud.com/doc/api/372/%E9%94%99%E8%AF%AF%E7%A0%81#1.E3.80.81.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81' title='公共错误码'>公共错误码</a>。
<tr>
<td> message <td> String <td> 错误信息
<tr>
<td> data <td> Array <td>返回的数组</td>
</tbody></table>

**data数组结构：**
<table class="t"><tbody><tr>
<th><b>参数名称</b></th>
<th><b>类型</b></th>
<th><b>描述</b></th>
<tr>
<td> data.requestId <td> UInt <td> 任务ID, 可通过<a href='/doc/api/260/1387' >DescribeTaskInfo</a>接口查询任务执行状态
</tbody></table>


## 4. 示例
```
https://redis.api.qcloud.com/v2/index.php?Action=ModfiyRedisPassword
&<公共请求参数>
&redisId=crs-ifmymj41
&oldPassword=49A2d!e@f12e
&password=12D3E@!r5ed
```
返回示例如下：
```
{
    "code": 0,
    "message": ""，
	"data": {
        "requestId": 11966
    }
}
```

