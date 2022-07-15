# bukkit消息源
**[Mesagisto信使项目](https://github.com/MeowCat-Studio/mesagisto)的一部分，消息转发客户端的bukkit(Minecraft)实现。**

## 安装

1. 在[Releases页面](https://github.com/MeowCat-Studio/bukkit-message-source/releases) 下载jar归档文件。

2. 将jar包移动至bukkit系服务端(如Spigot,Paper等)的plugins文件夹下。

3. 启动服务器,此时会自动生成配置文件。

4. 修改plugins/mesagisto/config.yml，
  参考
  ```yaml
  # 是否启用信使
  enable: true
  # 您的信使频道, 无论channel的值如何，
  # 只要保证不同转发客户端channel的值相同即可
  channel: test
  id-base: 0
  # 中间转发服务器,消息的桥梁.
  # 默认为我个人提供的[NATS](https://github.com/nats-io/nats-server)服务器
  nats:
    address: nats://itsusinn.site:4222
  # 加密设置
  cipher:
    # 加密用使用的密钥 需保证各端相同
    key: your-key
  ```

5. 保存配置文件，重启bukkit服务端。

## 注意事项
1. 与InteractiveChat的兼容性问题,请编辑plugins/InteractiveChat/config.yml
  找到
  ```yaml
  Settings:
    Bungeecord: false
    ChatListeningPlugins:
      - "Plugin:QuickShop, Class:.*, EventPriority:LOWEST"
      - "Plugin:Slimefun, Class:.*, EventPriority:LOWEST"
  ```
  在列表ChatListeningPlugins中添加`"Plugin:bukkit-message-source, Class:.*, EventPriority:LOWEST"`即
  ```yaml
  Settings:
    Bungeecord: false
    ChatListeningPlugins:
      - "Plugin:QuickShop, Class:.*, EventPriority:LOWEST"
      - "Plugin:Slimefun, Class:.*, EventPriority:LOWEST"
      - "Plugin:bukkit-message-source, Class:.*, EventPriority:LOWEST"
  ```
2. 对于Windows, 需要安装 [Microsoft Visual C++ 2010 Redistributable运行时](https://www.microsoft.com/en-us/download/details.aspx?id=26999)
