# tjuptatt_release

AzureQAQ's Blog: [3MoreDays](https://3moredays.com)

**tjuptatt** 是 [tjuptattendance](https://github.com/azureqaq/tjuptattendance/) 的一个特殊版本，
**暂时不在GitHub开源**，如果想 查看/使用 源码，请发送邮箱：[azureqaq](mailto:tjuptatt@3moredays.com) 并说明来意

## 简介
- 使用 [rust-lang](https://www.rust-lang.org/) 开发
- 支持所有主流平台 *部分平台需要自行编译*
- 针对 **TOP10** 签到优化
- 目前仅支持 **Windows**

## 目标

详细开发进度请查看: [changelog](./CHANGELOG.md)

- [ ] 更详细的配置文件及自定义功能
  - [x] 邮件功能
  - [ ] 信息查询
- [ ] TOP10优化
  - [x] 定时功能
  - [ ] 优化签到耗时

## 下载程序
本程序仅通过 [tjuptatt_release](https://github.com/azureqaq/tjuptatt_release) 发布编译好的程序
下载链接: [tjuptatt](https://github.com/azureqaq/tjuptatt_release/releases/latest/download/tjuptatt-x86_64-pc-windows-msvc.zip)

下载 `.zip` 文件，解压缩，得到程序本体 `tjuptatt.exe` 及帮助文件等

## 使用方法(手动)

### 临时使用
将不会保存 *cookies* 文件，相对于 *自动* 方式来说，稍微复杂一些，优点就是不会产生任何额外的文件

**注意：** 为了保证速度，此模式无法进行 TOP10 签到

1. 将得到的可执行文件 `tjuptatt.exe`：放到方便的位置
2. 打开命令行：切换到英文输入法，同时按下键盘上的 *Win + R* 键，打开 *CMD* 窗口，拖入 *可执行文件* 并在后边输入命令，比如：`C:\Users\user\Desktop\tjuptatt --help` 来查看帮助信息
3. 执行命令：`C:\Users\user\Desktop\tjuptatt -u "name" "password"` 来立即签到
4. 查看命令行输出

### 使用配置文件
支持 **TOP10** 签到
将保存配置及cookies到本地文件，方便使用

1. 初始化：`tjuptatt --init`
2. 按照 [示例](./config_template.toml) 编辑配置文件，配置文件路径在第一步时已经显示出来 *两个文件夹找一下* *config.toml*
3. 运行：`tjuptatt --top`，来进行 TOP10 签到 *程序会等待到最近一个TOP10时间点*
4. **可选-使用自定义位置的配置文件**：`tjuptatt -f 配置文件位置` *操作方式：可以先拖入tjuptatt再写-f，再拖入配置文件*
5. **注意：** 推荐在时间点前至少10秒钟启动程序，如果时间太短可能会直接导致失败


## 使用方法(自动)

请自行搜索或查看引用的教程：[计划任务](https://www.xitongcheng.com/jiaocheng/win10_article_47796.html)

**注意**：创建计划任务时，要添加参数的话，比如 `--email` `--top` 请在 *新建操作* 时，*程序或脚本* 填写 `tjuptatt` 的路径，*添加参数* 填写 `--email --top`

## 命令参数
**最简单的方式**:
- 立即签到: `tjuptatt -u "name" "password"` 或者 `tjuptatt` 不加任何参数
- TOP10签到：`tjuptatt --top`

### 参数
- `--init`: 初始化，创建默认配置文件及其父文件夹，创建保存cookie的文件夹
- `--uninstall`: 卸载，删除由`--init`所创建的文件和文件夹
- `--user`: 从命令行获取用户信息运行，格式: `--user id1 pwd1` 此种方式不需要 `--init` 即可正常使用，不会留下任何文件
- `--retry`: 签到重试次数，必须与 `--user` 一起使用 *暂时不推荐使用，因为豆瓣api得有一段时间冷却*
- `--file`: 使用配置文件的参数来进行签到，如果不指定则使用默认值，如果要使用自定义位置: `tjuptatt config -f CONFIG_PATH`，如果直接运行不加任何参数则效果如同: `tjuptatt -f DEFAULT_CONFIG_PATH`
- `--email`: 是否启用邮件通知，同时要求 *user* 填写了 `email` 字段，及邮件配置
- `--top`：是否开启TOP10签到模式 **必须填写好配置文件**

### 子命令 - config - 配置文件快速操作
- `--file`: 指定要操作的配置文件，如果不指定则使用默认值
- `--show`: 显示结果的配置文件简要信息
- `--adduser`: 快速添加用户，格式: `--adduser id1 pwd 1 --adduser id2 pwd2`
- `--rmuser`: 快速删除用户，格式: `--rmuser id1 --rmuser id2`

## 配置文件格式

可以参考配置文件模版: [配置文件模版](./config_template.toml)


## 如何参与开发
**注意：** 目前本项目使用纯 Rust 开发，也打算加入 Python 代码，来辅助开发

1. 如果你想贡献代码，也请联系邮箱 [azureqaq](mailto:tjuptatt@3moredays.com) 并附上你的GitHub主页链接
2. 等待GitHub邀请

## Q&A
1. 是否有在以后开源的打算？
  > 当然！但是目前我无法给出确切的时间。在有一定数量的人使用本程序时会在GitHub开源
2. 准确率？成功率？
  > 对于本程序使用的获取答案的方式来说，不能保证 **一直准确**, 成功率也不能保证很高

## 免责声明
- 本程序仅作为交流学习之用，对于使用本程序造成的后果，均由使用人承担
- 本程序不符合 [tjupt](https://tjupt.org) 的规定，如果造成封号等后果，自行承担
