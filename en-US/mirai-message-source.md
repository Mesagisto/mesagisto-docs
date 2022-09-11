# Mirai Message source

** Mirai is used for the function implementation of [Mesagisto](https://github.com/MeowCat-Studio/mesagisto), and the function is to forward messages to the client (Tencent QQ)**


## Requirement

- Mirai 2.12.0+, MCL 2.1.0+

- Front plugin [ChatCommand](https://github.com/project-mirai/chat-command)

- For Windows, [Microsoft Visual C + + 2010 redistributable](https://www.microsoft.com/en-us/download/details.aspx?id=26999) needs to be installed. The number of bits of runtime should be consistent with JDK


!!! Warning
    Messenger will automatically configure command permissions, please do not use permission command to operate messenger permissions (because it will be reset every time you start)
## Installation

=== "Manual installations"

	Download the jar archive on the [releases page](https://github.com/MeowCat-Studio/mirai-message-source/releases). Move to the plugins folder in the same directory of Mirai console (MCL).

=== "MCL auto install - stable"

	Using the MCL command `./mcl --update-package org.mesagisto:mirai-message-source --channel stable --type plugin`

	Use every time you start `./mcl -u` to update
=== "MCL auto install - pre"

	Using the MCL command `./mcl --update-package org.mesagisto:mirai-message-source --channel pre-release --type plugin`

	Use every time you start `./mcl -u` to update

  Note: since the pre release version is only released on GitHub release, [GH-Proxy](https://ghproxy.com/) is used


  However, access is still blocked in some regions. It is recommended to modify the MCL configuration file `config.json` Proxy options
## Simple introduction

1. Run MCL once and close it

2. Find the configuration file config/org.mesagisto.mirai-message-source/config.yml and modify
```yaml
# 中间转发服务器,消息的桥梁.
# 默认为信使公益[NATS](https://github.com/nats-io/nats-server)服务器
nats:
  address: 'nats://nats.mesagisto.org:4222'
# 加密设置
cipher:
  # 加密用使用的密钥
  key: your-key
# 网络代理, 下载Telegram或Discord图片时所需
# 注意, 如果tg-bot/dc-bot与mirai-bot在同一台主机
# 仅设置tg-bot/dc-bot的代理即可
proxy:
  # 是否启用代理
  enable: false
  # 代理服务器地址
  address: 'http://127.0.0.1:7890'
# 实验性权限配置
perm: 
  # 严格模式, 当启用时
  # 信使仅对下方users列表内用户所发命令作出响应
  # 当禁用时, 信使对所有用户所发指令作出响应
  # 但频道绑定仅允许管理员操作
  strict: false
  # 用户列表, QQ号
  users: 
    - 123456
# 存放信使频道与QQ群的对应关系,默认为空. 不推荐手动添加.
bindings: {}
```

3. 在 **QQ 群聊** (而不是 Mirai 控制台)中可以执行以下指令 `/msgist` 或 `/信使` 将会得到
```text
    参数不匹配, 你是否想执行: 
    /msgist about    (参数不足)
    /msgist ban <user>    (参数不足)
    /msgist bind <channel>    (参数不足)
    /msgist disable <group/channel>    (参数不足)
    /msgist enable <group/channel>    (参数不足)
    /msgist status    (参数不足)
    /msgist unban <user>    (参数不足)
    /msgist unbind    (参数不足)
```
4. 使用 /msgist bind 频道名 即可绑定到信使频道

## 注意事项
 1. 需要转发的消息源需要绑定同一个 ** 频道名**
 2. 黑名单功能需要开启严格模式
