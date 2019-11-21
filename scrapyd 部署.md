### scrapyd 部署

**注**：example 为项目名称

##### 安装

```
pip install scrapyd 
pip install scrapyd-client # 快速部署爬虫
pip install scrapyd-api # 集成python可调用api
pip install scrapydweb # web页面
pip install logparser # 日志解析
```

##### 启动 scrapyd

```
scrapyd -p example
```

##### 部署 爬虫

```
scrapyd-deploy -p example

scrapyd-deploy <target> -p example
```

##### 添加爬虫

```
curl http://localhost:6800/schedule.json -d project=example -d spider=dongtan
```

##### 取消爬虫

```
curl http://localhost:6800/cancel.json -d project=example -d job=68d25db0506111e9a4c0e2df1c2eb35b
# job 为可在web查看
```

##### 启动scrapyweb

```
# 第一次运行 一下命令 生成一个配置文件 scrapydweb_settings_v10.py
scrapydweb 
# 第二次运行 则进行运行 同目录下
scrapydweb 
```

##### 启动logparser

```
# 修改 scrapydweb_settings_v10.py 一下为Ture 会自动生成 stats.json 在日志目录下，可以重启一下scrapydweb
ENABLE_LOGPARSER = True

# 然后运行 就可以了
logparser 

```

##### scrapy.cfg

```
[settings]
default = example.settings
[deploy]
url = http://localhost:6800/
project = example
[deploy:djwq]
url = http://localhost:2100/
project = example
# scrapyd-deploy -p example
# scrapyd-deploy djwq -p example
```

