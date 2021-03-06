## 读取视频评论

#### 调用地址

http://api.bilibili.cn/feedback

#### 参数

|字段|必选|类型|说明|
|----|----|----|----|
|aid|true|int|AV号|
|page|true|int|页码|
|pagesize|false|int|单页返回的记录条数，最大不超过300，默认为10。|
|ver|false|int|API版本,最新是3|
|order|false|string|排序方式 默认按发布时间倒序 可选：good 按点赞人数排序 hot 按热门回复排序|

#### 返回

|返回值字段|字段类型|字段说明|
|----------|--------|--------|
|mid|int|会员ID|
|lv|int|楼层|
|fbid|int|评论ID|
|msg|string|评论信息|
|ad_check|int|状态 (0: 正常 1: UP主隐藏 2: 管理员删除 3: 因举报删除)|
|face|string|发布人头像|
|rank|int|发布人显示标识|
|uname|string|发布人暱称|


## 发布视频评论

#### 调用地址

http://api.bilibili.cn/feedback/post

需要 App Key 并验证登录状态(Access key)；要求应用申请评论权限

#### 参数

|字段|必选|传递方式|类型|说明|
|----|----|--------|----|----|
|mid|true|POST|int|发布帐号(必须与access_key帐号一致)|
|msg|true|POST|int|发布的信息|
|mode|false|GET|string|发布的评论类型(topic 话题 news 新闻 arc 视频)|
|aid/tp_id/news_id|true|GET|int|要发布评论的投稿编号 (视发布的类型而定 topic使用tp_id news使用news_id 视频使用aid)|
|quoteID|false|POST|int|引用的评论ID|
|captcha|false|POST|string|当服务器返回错误代码-105时 需要要求用户输入验证码|

#### 错误代码

|代码|说明|
|----|----|
|-632|单次AT的人数过多|
