FROM python:latest

RUN sed -i 's/deb.debian.org/mirrors4.tuna.tsinghua.edu.cn/' /etc/apt/sources.list \
 && sed -i 's/security.debian.org/mirrors4.tuna.tsinghua.edu.cn/' /etc/apt/sources.list \
 && apt-get update \
 && apt-get install -y locales linux-headers-amd64 apt-utils \
 && rm -rf /var/lib/apt/lists/* \
 && localedef -i zh_CN -c -f UTF-8 -A /usr/share/locale/locale.alias zh_CN.UTF-8 \
 && pip install -i https://pypi.tuna.tsinghua.edu.cn/simple -U pip \
 && pip install -i https://pypi.tuna.tsinghua.edu.cn/simple python-dotenv uwsgi flask geoip2 aiofiles \
 && apt-get -y remove linux-headers-amd64 \
 && apt-get -y autoremove

ENV LC_ALL zh_CN.UTF-8
ENV LANG zh_CN.UTF-8
