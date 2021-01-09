From node:lts-alpine

ENV CODE_VERSION 1.52.1

RUN apk add --no-cache --virtual .build-deps-code \
	g++ \
	make \
	libx11-dev \
	libxkbfile-dev \
	libsecret-dev \
	python \
	git \
    && wget https://github.com/microsoft/vscode/archive/$CODE_VERSION.tar.gz \
    && tar xzf $CODE_VERSION.tar.gz -C /opt/ \
    && rm $CODE_VERSION.tar.gz \
    && cd /opt/vscode-$CODE_VERSION \
    && yarn \
    && apk del .build-deps

EXPOSE 8080

CMD ["yarn", "--no-launch"]
