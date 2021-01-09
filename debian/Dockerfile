From node:lts-buster
#WORKDIR /opt
#ADD https://archive.fastgit.org/microsoft/vscode/archive/1.52.1.tar.gz /app
ENV CODE_VERSION 1.52.1

RUN sed -i 's/deb.debian.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list \
    && sed -i 's/security.debian.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list \
    && apt-get update \
    && apt-get install -y build-essential \
	g++ \
	libx11-dev \
	libxkbfile-dev \
	libsecret-1-dev \
        apt-utils \
    && wget https://archive.fastgit.org/microsoft/vscode/archive/$CODE_VERSION.tar.gz \
    && tar xzf $CODE_VERSION.tar.gz -C /opt/ \
    && rm $CODE_VERSION.tar.gz \
    #&& ls -al ~ \
    #&& sleep 5 \
    && cd /opt/vscode-$CODE_VERSION
    #&& npm config set registry https://registry.npm.taobao.org

RUN cd /opt/vscode-$CODE_VERSION \
    #&& yarn config set registry https://registry.npm.taobao.org \
    && yarn
#--non-interactive --force --audit --frozen-lockfile --prod

EXPOSE 8080

CMD ["yarn" "--no-launch"]
