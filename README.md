### TELEMBY
##### A simple Telegram Bot for Emby
###### Powered by Docker

This is a simple python-based bot to carry out some trivial Emby tasks and retrieve some data.

For ease, it is held inside a Docker Container.

It is configured to only allow input from one user (i.e You) so you need to specify your telegram user id in the config.

N.B - This has been done with approx 1 weeks worth of python under my belt, so the code may be (is) ugly!

### Known Issues:
- Json formatting isn't pretty

### To Do:
- Slim down the base image
- Search Library
- Add/Disable Users
- Reset User Passwords 

### Setup:

#### Telegram  
- Retrieve your Telegram UID using a tool such as JSON Dump Bot
- Create a Bot Using Botfather
- Retrieve your Bot Token
- Edit the bots commands in botfather and paste in the below:

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


