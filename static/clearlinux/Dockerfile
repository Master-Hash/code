FROM node:lts as element-web

# element-web
# https://github.com/vector-im/element-web/tree/master
ARG ELEMENT_VERSION=1.7.21

# Support custom branches of the react-sdk and js-sdk. This also helps us build
# images of element-web develop.
ARG USE_CUSTOM_SDKS=false
ARG REACT_SDK_REPO="https://github.com/matrix-org/matrix-react-sdk.git"
ARG REACT_SDK_BRANCH="master"
ARG JS_SDK_REPO="https://github.com/matrix-org/matrix-js-sdk.git"
ARG JS_SDK_BRANCH="master"

RUN apt-get update && apt-get install -y git \
 # These packages are required for building Canvas on architectures like Arm
 # See https://www.npmjs.com/package/canvas#compiling
  build-essential libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev \
 && cd /opt \
 && git clone --depth=1 -b v${ELEMENT_VERSION} https://github.com/vector-im/element-web.git

COPY config.json /opt/element-web/
WORKDIR /opt/element-web
RUN yarn && yarn build
# 毕竟这个阶段都完了，git 就不删了吧（不是

FROM clearlinux/httpd:alpine

# 静态站点：
# element-web
# adarkroom（不过这个不在这里装，而是自己手动 fetch？）

# 动态站点：还不清楚自己想装什么呢，WP 已经有点烦了（

COPY --from=element-web /opt/element-web/webapp /var/www/element-web
