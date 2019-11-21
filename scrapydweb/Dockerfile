FROM python:3.6

RUN pip install -i https://pypi.douban.com/simple scrapydweb

COPY . /code

WORKDIR /code

CMD scrapydweb
