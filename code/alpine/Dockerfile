FROM node:lts-alpine

ENV CODE_VERSION 1.53.0

RUN apk add --no-cache --virtual .build-deps-code \
        build-base \
        libx11-dev \
        libxkbfile-dev \
        libsecret-dev \
        python \
        git \
    && cd /opt \
    && git clone -b ${CODE_VERSION} --depth=1 https://github.com/microsoft/vscode.git \
    && cd vscode \
    && yarn \
    && apk del .build-deps-code \
    && rm -rf /var/cache/apk/*

EXPOSE 8080
WORKDIR /opt/vscode
CMD ["yarn", "web", "--no-launch"]
