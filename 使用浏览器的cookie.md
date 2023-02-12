## 使用浏览器的cookie

### 一、提取浏览器cookie

#### 准备

请确保浏览器能够正常登录tjupt，即具有有效cookie

安装插件(任选一种即可)：

- Edge：[Cookie Editor - Microsoft Edge Addons](https://microsoftedge.microsoft.com/addons/detail/cookie-editor/ajfboaconbpkglpfanbmlfgojgndmhmc)
- Chrome: 插件商店搜索 **EditThisCookie**

#### 提取cookie

1. 浏览器访问tjupt
2. 使用插件的cookie导出功能

得到的cookie形式可能如下：

```json
[
{
    "domain": ".tjupt.org",
    "expirationDate": 1683000.80080,
    "hostOnly": false,
    "httpOnly": false,
    "name": "access_token",
    "path": "/",
    "sameSite": "unspecified",
    "secure": false,
    "session": false,
    "storeId": "1",
    "value": "COOKIE_VALUE",
    "id": 1
}
]
```

需要的数据为：`value` 对应的 `COOKIE_VALUE` (不需要两头的双引号)

### 二、写入tjuptatt的cookie文件

tjuptatt 储存cookies的文件夹为：`C:\Users\USERNAME\AppData\Local\tjuptatt`，如果没有可以手动创建，(其中 `USERNAME` 为电脑上你的用户名)

这个文件夹下存放使用过的cookies文件，文件名称形如：`username_cookie.json`，如果不存在，请手动创建，比如你的tjupt账号名字是：“zhangsan”，则文件名为：`zhangsan_cookie.json`

如果无法编辑扩展名，请自行百度。

请确保为 `utf-8` 编码。 **Win10或更旧的系统，请勿使用自带文本编辑器，推荐使用 notepad3**

将其中内容全部删除，按照格式填入数据：

```json
{"raw_cookie":"access_token=COOKIE_VALUE; Path=/; Domain=tjupt.org; Max-Age=604800","path":["/",true],"domain":{"Suffix":"tjupt.org"},"expires":{"AtUtc":"2023-03-23T04:15:59Z"}}
```

替换其中的 `COOKIE_VALUE`，并修改 `AtUtc` 为 **今后** 的UTC时间点，其中 `Max-Age` 为cookie有效期，可以适当修改，单位为秒。

如果有什么问题或建议，欢迎 issue 或 pr ！
