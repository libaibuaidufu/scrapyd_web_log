FROM python:3.6
RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' >/etc/timezone
RUN pip install -i https://pypi.douban.com/simple scrapydweb

COPY . /code

WORKDIR /code

CMD scrapydweb
