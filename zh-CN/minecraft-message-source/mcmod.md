# MCMod消息源

**[Mesagisto信使项目](https://github.com/MeowCat-Studio/mesagisto)的一部分，消息转发客户端的mcmod(Minecraft)实现。**

## 需求

=== "Fabric 1.16-1.19"

	- 对于Windows, 需要安装 [Microsoft Visual C++ 2010 Redistributable运行时](https://www.microsoft.com/en-us/download/details.aspx?id=26999) 运行时位数应与JDK保持一致
	- 前置依赖 [Fabric-API](https://www.curseforge.com/minecraft/mc-mods/fabric-api) 任意版本

=== "Forge1.18"

	- 对于Windows, 需要安装 [Microsoft Visual C++ 2010 Redistributable运行时](https://www.microsoft.com/en-us/download/details.aspx?id=26999) 运行时位数应与JDK保持一致

## 安装

1. 在[Releases页面](https://github.com/Mesagisto/mcmod-message-source/releases)下载jar归档文件。
2. 将jar包移动至fabric/forge服务端的mods文件夹下。
3. 启动服务器,此时会自动生成配置文件。
4. 修改mods/mesagisto/config.yml，
    参考

  ```yaml
  # 是否启用信使
  enable: true
  # 您的信使频道, 无论channel的值如何，
  # 只要保证不同转发客户端channel的值相同即可
  channel: "your-channel"
  # 服务器的TargetName, 具有相同Target的群聊/服务器不会显示彼此的消息
  # 这对于那些安装了子服间消息互通的服务器可能很有用
  target: "target-name"
  # 中间转发服务器,消息的桥梁.
  # 默认为信使公益[NATS](https://github.com/nats-io/nats-server)服务器
  nats:
    address: nats://nats.mesagisto.org:4222
  # 加密设置
  cipher:
    # 加密用使用的密钥 需保证各端相同
    key: default-key
  ```
5. 启动fabric/forge服务端。

## 注意事项

1. 暂无
