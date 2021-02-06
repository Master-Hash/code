FROM node:lts

COPY release.diff /opt/

ENV CODE_VERSION 1.53.0

RUN apt-get update \
    && apt-get install -y build-essential \
        g++ \
        libx11-dev \
        libxkbfile-dev \
        libsecret-1-dev \
        apt-utils \
        git \
    && rm -rf /var/lib/apt/lists/* \
    && cd /opt \
    && git clone -b ${CODE_VERSION} --depth=1 https://github.com/microsoft/vscode.git \
    && cd vscode \
    && patch -p0 < ../release.diff \
    && yarn

EXPOSE 8080
WORKDIR /opt/vscode
CMD ["yarn", "web", "--no-launch"]
