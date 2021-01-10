From node:lts
#WORKDIR /opt
#ADD https://archive.fastgit.org/microsoft/vscode/archive/1.52.1.tar.gz /app
ENV CODE_VERSION 1.52.1

RUN apt-get update \
    && apt-get install -y build-essential \
	g++ \
	libx11-dev \
	libxkbfile-dev \
	libsecret-1-dev \
        apt-utils \
        git \
    #&& wget https://github.com/microsoft/vscode/archive/$CODE_VERSION.tar.gz \
    #&& tar xzf $CODE_VERSION.tar.gz -C /opt/ \
    #&& rm $CODE_VERSION.tar.gz \
    && cd /opt \
    && git clone https://github.com/microsoft/vscode.git \
    && git checkout $CODE_VERSION \
    #&& ls -al ~ \
    #&& sleep 5 \
    && cd vscode \
    #&& npm config set registry https://registry.npm.taobao.org
    #&& yarn config set registry https://registry.npm.taobao.org \
    && yarn
#--non-interactive --force --audit --frozen-lockfile --prod

EXPOSE 8080
WORKDIR /opt/vscode
CMD ["yarn" "--no-launch"]
