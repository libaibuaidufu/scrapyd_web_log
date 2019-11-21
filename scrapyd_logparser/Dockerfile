FROM python:3.6

RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' >/etc/timezone

COPY requirements.txt /opt

RUN pip install --upgrade pip -i https://pypi.douban.com/simple/
RUN pip install -r /opt/requirements.txt -i https://pypi.douban.com/simple/
RUN mkdir /etc/scrapyd && mkdir /root/logs
COPY scrapyd.conf /etc/scrapyd
CMD scrapyd & logparser
