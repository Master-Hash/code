From node:lts-alpine
#WORKDIR /opt
#ADD https://archive.fastgit.org/microsoft/vscode/archive/1.52.1.tar.gz /app
ENV CODE_VERSION 1.52.1

RUN apk add --no-cache --virtual .build-deps-code \
	g++ \
	make \
	libx11-dev \
	libxkbfile-dev \
	libsecret-dev \
	python \
    && wget https://github.com/microsoft/vscode/archive/$CODE_VERSION.tar.gz \
    && tar xzf $CODE_VERSION.tar.gz -C /opt/ \
    && rm $CODE_VERSION.tar.gz \
    && cd /opt/vscode-$CODE_VERSION \
    #&& yarn config set registry https://registry.npm.taobao.org \
    && yarn \
    && apk del .build-deps

EXPOSE 8080

CMD ["yarn", "--no-launch"]
