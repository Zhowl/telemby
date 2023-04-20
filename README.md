### TELEMBY
##### 一个用于 Emby 的简单 Telegram 机器人
###### Powered by Docker

This is a simple python-based bot to carry out some trivial Emby tasks and retrieve some data.

For ease, it is held inside a Docker Container.

It is configured to only allow input from one user (i.e You) so you need to specify your telegram user id in the config.

N.B - This has been done with approx 1 weeks worth of python under my belt, so the code may be (is) ugly!

这是一个基于 Python 的简单机器人，可执行一些琐碎的 Emby 任务并检索一些数据。

为方便起见，它被包含在一个 Docker 容器中。

它配置为仅允许来自一个用户（即您）的输入，因此您需要在配置中指定您的 Telegram 用户 ID。

注 - 这是在我手头大约一周的 Python 经验下完成的，所以代码可能很丑陋！

### Known Issues:
- Json formatting isn't pretty JSON 格式不美观

### To Do:
- Slim down the base image	精简基础镜像
- Search Library		搜索库
- Add/Disable Users		添加/禁用用户
- Reset User Passwords 		重置用户密码

### Setup:

#### Telegram  
- Retrieve your Telegram UID using a tool such as JSON Dump Bot		使用 JSON Dump Bot 等工具检索您的 Telegram UID
- Create a Bot Using Botfather						使用 Botfather 创建一个 Bot
- Retrieve your Bot Token						检索您的 Bot Token
- Edit the bots commands in botfather and paste in the below:		在 botfather 中编辑机器人命令，并粘贴以下内容：

```
status - EMBY服务器状态
refreshlibrary - 刷新全部媒体库
refreshguide - 刷新电视指南数据
users - EMBY用户列表
devices - EMBY设备列表
activity - 最后10个活动项目
backup - 触发备份
help - 机器人帮助
```
    
#### Docker

##### From Source

- Clone this Repo
- Add your details to ./app/config.ini - eg:
	
	```
	
		[BOT]

		API_TOKEN =  8079943032202020131323321323
		USER_ID = 123456

		[EMBY]

		SERVER = http://emby.media:8096/
		API_KEY = 5454545454549abedea814939dad
  	```

- Build the Image:
    ` docker build -t telemby .`
   
- Run Container from Image
    `docker run -d --name=telemby telemby`
    
##### From DockerHub

您需要在 docker run 命令中指定配置变量：

- BOT: Telegram Bot Token
- USER: Telegram User ID
- SERVER: EMBY 服务器地址 - 这必须 http(s):// 前缀和斜杠（见下面的例子）
- API: Emby API Key


`docker run -d --env BOT=BOTTOKEN--env USER=TELEGRAM-UID--env SERVER=http://emby-server.domain:port/ --env API=EMBY-API-KEY --name telemby matty87a/telemby`


