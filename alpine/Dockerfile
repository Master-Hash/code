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
    && cd /opt
    && git clone https://github.com/microsoft/vscode.git \
    && git checkout $CODE_VERSION \
    && cd vscode \
    && yarn \
    && apk del .build-deps

EXPOSE 8080
WORKDIR /opt/vscode
CMD ["yarn", "--no-launch"]
