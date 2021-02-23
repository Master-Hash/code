FROM python:latest

COPY postcard opt/postcard
COPY GeoLite2-City.mmdb opt/postcard/
COPY postcard.ini opt/postcard

RUN sed -i 's/deb.debian.org/mirrors4.tuna.tsinghua.edu.cn/' /etc/apt/sources.list \
 && sed -i 's/security.debian.org/mirrors4.tuna.tsinghua.edu.cn/' /etc/apt/sources.list \
 && apt-get update \
 && apt-get install -y locales linux-headers-amd64 apt-utils \
 && rm -rf /var/lib/apt/lists/* \
 && localedef -i zh_CN -c -f UTF-8 -A /usr/share/locale/locale.alias zh_CN.UTF-8 \
 && pip install -i https://pypi.tuna.tsinghua.edu.cn/simple -U pip \
 && pip install -i https://pypi.tuna.tsinghua.edu.cn/simple python-dotenv uwsgi flask geoip2 \
 && apt-get -y remove linux-headers-amd64 \
 && apt-get -y autoremove

ENV LC_ALL zh_CN.UTF-8
ENV LANG zh_CN.UTF-8
WORKDIR /opt/postcard

ENV FLASK_APP app
ENV FLASK_ENV production

EXPOSE 5000

CMD [ "uwsgi", "postcard.ini" ]
