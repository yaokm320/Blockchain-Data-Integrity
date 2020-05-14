FROM python:3.6-alpine

RUN adduser -D webportal

WORKDIR /home/webportal

# 报错使用下面修改的
# RUN apk --update add alpine-sdk postgresql py-psycopg2 postgresql-dev libffi-dev gmp-dev

############################ 修改
RUN echo -e "http://nl.alpinelinux.org/alpine/v3.9/main\nhttp://nl.alpinelinux.org/alpine/v3.9/community" > /etc/apk/repositories
RUN apk update
RUN apk add alpine-sdk 
RUN apk add postgresql 
RUN apk add py-psycopg2 
RUN apk add postgresql-dev 
RUN apk add libffi-dev 
RUN apk add gmp-dev
############################## 完毕

COPY requirements.txt requirements.txt
RUN python -m venv venv
RUN venv/bin/pip install -U pip setuptools

### 安装cioncurve依赖包和coincurve
RUN venv/bin/pip install asn1crypto
RUN venv/bin/pip install cffi 
RUN venv/bin/pip install pycparser
RUN venv/bin/pip install coincurve

RUN venv/bin/pip install -r requirements.txt

COPY app app
COPY migrations migrations
COPY webportal.py config.py boot.sh ./
RUN chmod a+x boot.sh

ENV FLASK_APP webportal.py

RUN chown -R webportal:webportal ./
USER webportal

EXPOSE 5000
ENTRYPOINT ["./boot.sh"]
