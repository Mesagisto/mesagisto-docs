 

# bungee消息源

**[Mesagisto信使项目](https://github.com/MeowCat-Studio/mesagisto)的一部分，消息转发客户端的bungee(Minecraft)实现。**

## 需求
- 对于Windows, 需要安装 [Microsoft Visual C++ 2010 Redistributable运行时](https://www.microsoft.com/en-us/download/details.aspx?id=26999) 运行时位数应与JDK保持一致

## 安装

1. 在[Releases页面](https://github.com/MeowCat-Studio/bungee-message-source/releases) 下载jar归档文件。

2. 将jar包移动至bungeecord系服务端(如Waterfall等)的plugins文件夹下。

3. 启动服务器,此时会自动生成配置文件, {==关闭服务器==}。

4. 修改plugins/mesagisto/config.yml，

    ```yaml
    # 是否启用信使
    enable: true
    # 您的信使频道绑定
    # 可手动编辑,但建议通过指令添加
    bindings:
      # 服务器名: 信使频道
      sub1: "test"
      sub2: "test"
    # 加密设置
    cipher:
      # 加密用使用的密钥 {==需保证各端相同==}
      key: "default"
    # id计数器
    idCounter:
      sub1: 7
      sub2: 3
    # 中间转发服务器,消息的桥梁.
    # 默认为我个人提供的[NATS](https://github.com/nats-io/nats-server)服务器
    nats: "nats://nats.mesagisto.org:4222"
    # 消息模板
    template:
      message: "§7<{{sender}}> {{content}}"
    ```

5. 保存配置文件，启动服务器。

6. 
    - 在需要设置信使的子服内使用`/msgist help`查看帮助
    - 使用`/msgist [频道名]`绑定信使频道

## 注意事项

1. 权限管理,本插件的权限节点为`mesagisto`, 若想使用信使的命令需要授予该权限

=== "不使用权限管理插件"

    修改bungee配置文件config.yml为
    ```yaml
    permissions:
      admin:
      - some-other-perm
      - {++mesagisto++}
    ......
    groups:
      playername:
      - default
      - {++admin++}
    ```

=== "使用权限管理插件"

    文档待补充
