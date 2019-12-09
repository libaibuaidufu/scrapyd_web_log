FROM python:3.6

RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' >/etc/timezone

RUN echo "deb http://mirrors.aliyun.com/debian/ jessie main non-free contrib \
deb http://mirrors.aliyun.com/debian/ jessie-proposed-updates main non-free contrib \
deb-src http://mirrors.aliyun.com/debian/ jessie main non-free contrib \
deb-src http://mirrors.aliyun.com/debian/ jessie-proposed-updates main non-free contrib" > /etc/apt/sources.list \
	&& apt-get update \
	&& apt-get install -y supervisor
	
RUN mkdir /etc/scrapyd && mkdir /root/logs
COPY supervisord.conf /etc/supervisor/conf.d
COPY requirements.txt /opt
COPY scrapyd.conf /etc/scrapyd
RUN pip install --upgrade pip -i https://pypi.douban.com/simple/
RUN pip install -r /opt/requirements.txt -i https://pypi.douban.com/simple/
EXPOSE 6800
CMD supervisord



