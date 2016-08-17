
## initWithAppID

```
- (instancetype)initWithAppID:(int)appID
                andAppVersion:(NSString *)appVersion
                andAppChannel:(NSString *)appChannel;
```
接口说明：初始化Wns系统
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| appID | int | 是 | WNS控制台分配给app的id |
| appVersion | NSString | 否 | app的版本号 |
| appChannel | NSString | 否 | app的发布渠道信息:该值填"DEBUG"和"RDM"时, 后台会分别使用DEBUG和RDM证书进行苹果推送, 填其它值时, 默认使用正式的证书来进行苹果推送 |


## reset
```
- (void)reset:(BOOL)reconnect;
```
接口说明：重置wns连接
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| reconnect | BOOL | 是 | 重置连接方式 YES：先关闭现有WNS通道再重新建立  NO：只关闭现有WNS通道 |


## setStatusCallback
```
- (void)setStatusCallback:(WnsStatusCallback)callback;

typedef void (^WnsStatusCallback)(WnsSDKStatus status);

typedef NS_ENUM(NSInteger, WnsSDKStatus) {
    WnsSDKStatusDisconnected    = 0,    //Wns通道不可用
    WnsSDKStatusConnecting      = 1,    //Wns通道建立中
    WnsSDKStatusConnected       = 2,    //Wns通道建立成功
};

```
接口说明：获取wns网络状态
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| callback | WnsStatusCallback | 是 | 在WnsStatusCallback回调block中同步当前wns通道状态|


## setLogCallback
```
- (void)setLogCallback:(WnsLogCallback)callback;

typedef void (^WnsLogCallback)(NSString *log, WnsSDKLogLevel level);

typedef NS_ENUM(NSInteger, WnsSDKLogLevel) {
    WnsSDKLogLevelDisabled      = -1,
    WnsSDKLogLevelError         = 0,
    WnsSDKLogLevelWarn          = 1,
    WnsSDKLogLevelInfo          = 2,
    WnsSDKLogLevelDebug         = 3,
    WnsSDKLogLevelMax           = 4,
};

```
接口说明：获取wns sdk记录的本地log信息
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| callback | WnsLogCallback | 是 | 在WnsLogCallback回调block中获取wns sdk记录在本地的log信息|

## bind
```
- (void)bind:(NSString *)uid completion:(void(^)(NSError *error))completion;
```
接口说明：绑定开发商用户id到wns系统中
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| uid | NSString | 是 | 开发商自己的用户id|
| completion | block | 是 | 调用结果的回调block|


## unbind
```
- (void)unbind:(NSString *)uid completion:(void(^)(NSError *error))completion;
```
接口说明：从wns系统中解绑开发商用户id
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| uid | NSString | 是 | 开发商自己的用户id|
| completion | block | 是 | 调用结果的回调block|


## sendRequest
```
- (long)sendRequest:(NSData *)data
                cmd:(NSString *)cmd
            timeout:(unsigned int)timeout
         completion:(void(^)(NSString *cmd, NSData *data, NSError *bizError, NSError *wnsError, NSError *wnsSubError))completion;
```
接口说明：调用后端接口服务(二进制协议)
返回值：

```
	-1 : 失败
	long : 请求的序列号
```
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| cmd | NSString | 是 | 接口命令字|
| timeout | unsigned int | 是 | 调用超时时间|
| completion | block | 是 | 调用结果的回调block|
| completion (cmd) | NSString | 是 | 回调中的命令字|
| completion (data) | NSData | 是 | 回调中后端返回的数据|
| completion (bizError) | NSError | 是 | 回调中开发商的返回码|
| completion (wnsError) | NSError | 是 | 回调中wns的主返回码|
| completion (wnsSubError) | NSError | 是 | 回调中wns的子返回码|


## sendHTTPRequest
```
- (long)sendHTTPRequest:(NSURLRequest *)request
                    cmd:(NSString *)cmd
                timeout:(unsigned int)timeout
             completion:(void (^)(NSString *cmd, NSURLResponse* response, NSData* data, NSError* wnsError, NSError *wnsSubError))completion;
```
接口说明：调用后端接口服务(HTTP协议)
返回值： 

```
	-1 : 失败
	long : 请求的序列号
```
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| request | NSURLRequest | 是 | 系统NSURLRequest对象 |
| cmd | NSString | 是 | 接口命令字|
| timeout | unsigned int | 是 | 调用超时时间|
| completion | block | 是 | 调用结果的回调block|
| completion (cmd) | NSString | 是 | 回调中的命令字|
| completion (response) | NSURLResponse | 是 | 回调中后端返回的数据转化为NSURLResponse|
| completion (data) | NSData | 是 | 回调中后端返回的原始数据|
| completion (wnsError) | NSError | 是 | 回调中wns的主返回码|
| completion (wnsSubError) | NSError | 是 | 回调中wns的子返回码|



## cancelRequest
```
- (void)cancelRequest:(long)seqno;
```
接口说明：取消请求
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| seqno | long | 是 | 请求序列号，从sendRequest或sendHTTPRequest调用返回的序列号 |


## cancelAllRequest
```
- (void)cancelAllRequest;
```
接口说明：取消所有请求


## setPushDataReceiveBlock
```
- (void)setPushDataReceiveBlock:(void(^)(NSString *cmd, NSData *data, NSError *error))completion;
```
接口说明：设置Wns Push数据的数据接收回调block
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| completion (cmd) | NSString | 是 |  push数据的的命令字|
| completion (data) | NSData | 是 |  push的具体数据|
| completion (error) | NSError | 是 |  异常对象|


## registerRemoteNotification
```
- (void)registerRemoteNotification:(NSString *)deviceToken completion:(void(^)(NSError *error))completion;
```
接口说明：在wns系统注册苹果的推送服务所使用的devicetoken
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| deviceToken | NSString | 是 |  push数据的的命令字|
| completion (data) | block | 是 |  注册结果回调|


## setLogLevel
```
- (void)setLogLevel:(WnsSDKLogLevel)level;

typedef NS_ENUM(NSInteger, WnsSDKLogLevel) {
    WnsSDKLogLevelDisabled      = -1,
    WnsSDKLogLevelError         = 0,
    WnsSDKLogLevelWarn          = 1,
    WnsSDKLogLevelInfo          = 2,
    WnsSDKLogLevelDebug         = 3,
    WnsSDKLogLevelMax           = 4,
};

```
接口说明：设置log级别,数值越大越详细
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| level | WnsSDKLogLevel | 是 |  具体的log级别|


## log
```
- (void)log:(WnsSDKLogLevel)level file:(const char *)file func:(const char *)func line:(int)line module:(NSString*)module EFDict:(NSDictionary *)extDict msg:(NSString *)fmt, ...;

typedef NS_ENUM(NSInteger, WnsSDKLogLevel) {
    WnsSDKLogLevelDisabled      = -1,
    WnsSDKLogLevelError         = 0,
    WnsSDKLogLevelWarn          = 1,
    WnsSDKLogLevelInfo          = 2,
    WnsSDKLogLevelDebug         = 3,
    WnsSDKLogLevelMax           = 4,
};

```
接口说明：记录日志信息
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| level | WnsSDKLogLevel | 是 |  具体的log级别|
| file | onst char * | 是 |  记录log处位置对应的文件名|
| func | const char * | 是 |  记录log处位置对应的函数名|
| line | int | 是 |  记录log处位置对应的文件行号|
| module | NSString | 是 |  记录log处位置对应的模块名|
| extDict | NSDictionary | 是 | 按k/v格式存储的log信息 |
| fmt | NSString | 是 |  动态参数的log信息|


## setAutoTestMode
```
- (void)setAutoTestMode:(BOOL)isEnable;
```
接口说明：设置自动测速模式，测速模式下，开发商自己的接口不用接入wns系统，wns sdk会定时发模拟包到wns后台，这样开发商可以评估正式接入后的效果。
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| isEnable | BOOL | 是 |  是否启用|


## setDebugIP
```
- (void)setDebugIP:(NSString *)ip port:(unsigned short)port;
```
接口说明：使用测试环境，测试环境下终端连接到wns测试环境，wns测试环境也会使用开发商的测试服务器(控制台上配置)
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| ip | NSString | 是 |  使用固定IP : 183.60.76.15|
| port | unsigned short | 是 |  可选的端口：80或0|


## reportDebugLog
```
- (void)reportDebugLog:(NSString *)title content:(NSString *)content beginTime:(NSTimeInterval)beginTime endTime:(NSTimeInterval)endTime;
```
接口说明：将wns sdk记录在终端的log和用户指定的内容上报到wns后台(可以在控制台查看上报的log信息)
参数说明：

| 参数 | 类型 | 必选 | 说明 |
|---------|---------|---------|---------|
| title | NSString | 是 |  log上报的标题|
| content | NSString | 是 |  指定上报的内容，不需要可为空(sdk会自动再加上本地sdk记录的log一起上报)|
| beginTime | NSTimeInterval | 是 |  上报从这个时间开始的本地log|
| endTime | NSTimeInterval | 是 |  这个时间后的log不上报|


## getWnsCarrierType
```
- (WnsSDKCarrierType)getWnsCarrierType;

typedef NS_ENUM(NSInteger, WnsSDKCarrierType) {
    WnsSDKCarrierUnknown        = 0, //未知
    WnsSDKCarrierMobile         = 1, //移动
    WnsSDKCarrierUnicom         = 2, //联通
    WnsSDKCarrierTelecom        = 3, //电信
    WnsSDKCarrierTietong        = 4  //铁通
};

```
接口说明：取得运营商信息
返回值： 

```
	WnsSDKCarrierType : 运营商信息
```


## wid
```
- (int64_t)wid;
```
接口说明：获取当前用户的wid
返回值： 

```
	int64_t : 用户的wid
```

## keyLog
```
- (NSString *)keyLog;
```
接口说明：获取sdk记录的关键步骤信息，和debug log的区别是只记录关键信息，便于理解和快速查看
返回值： 

```
	NSString : 具体的信息
```





















































































































































