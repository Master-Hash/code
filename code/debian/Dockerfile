FROM node:lts


ENV CODE_VERSION 1.52.1

RUN apt-get update \
    && apt-get install -y build-essential \
	g++ \
	libx11-dev \
	libxkbfile-dev \
	libsecret-1-dev \
        apt-utils \
        git \
    && cd /opt \
    && git clone -b ${CODE_VERSION} --depth=1 https://github.com/microsoft/vscode.git \
    && cd vscode \
    && yarn

EXPOSE 8080
WORKDIR /opt/vscode
CMD ["yarn", "web", "--no-launch"]