#### scrapy + scrapyd + scrapydweb + logparser 分布式部署

##### 1.构建 scrapyd_logparser

```
cd scrapyd_logparser
docker build -t scrapyd_logparser .
```

##### 2.运行 scrapyd_logparser

```
docker run -d -p 6800:6800 --name scrapyd_1 scrapyd_logparser
# docker run -d -p 6800:6800 -v /root/scrapyd_logparser:/code --name scrapyd_1 scrapyd_logparser
# 可以外联出文件 可以进行配置修改
```

##### 3.构建 scrapydweb

```
cd scrapydweb
docker build -t scrapydweb .
```

##### 4.运行 scrapydweb

```
docker run -d -p 5000:5000 -v /root/scrapydweb:/code --name scrapydweb scrapydweb
# 外链出文件 好修改配置 进行更新部署
# 修改配置
vim scrapydweb_settings_v10.py 
# 重启
docker restart scrapydweb
```

##### 5.多机部署

```
在其他机器中 部署 文件 执行 1，2 步
同时在 scrapydweb 的配置文件 添加在 新主机的ip

# 以下添加
SCRAPYD_SERVERS = [
    '192.168.5.131:6800',
	'192.168.5.131:6805',
    # 'username:password@localhost:6801#group',
    # ('username', 'password', 'localhost', '6801', 'group'),
]

```

**注**： 可以自己查看 一下 scrapydweb 配置文件 修改，和 scrapyd 配置文件修改

参考：

1. [scrapydweb](https://github.com/my8100/scrapydweb )
2. [logparser](https://github.com/my8100/logparser )