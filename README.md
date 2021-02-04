# code

## 用于自动构建
许多 Dockerfiles 杂乱地堆在一起。

可用/计划中：
- [code](https://github.com/microsoft/vscode)
- [openlitespeed](https://openlitespeed.org/)
- [deno](https://deno.land/)

很多镜像的本地构建过程需要修改系统/语言包管理器，如有需要，请自行修改。本仓库专用于 Docker hub 自动构建，故压缩镜像体积乃第一要务。

如果对任何抛出的问题有答案，或者不能理解其它的备注，请开 issue。后者我会附上链接和更详细的说明。

## 用于本地环境搭建
这些 Dockerfiles 就纯属~~自娱自乐~~个人备份啦（

可用：
- archlinux:docs（基于 archlinux，装有 texlive，pandoc，tree，emacs，使用 tuna 源）

## 用于个人服务器
不太确定是否应该公开放出来。

可能会有：
- static（基于 clearlinux/httpd 或者 httpd:alpine，再加装一些静态站点，比如 element-web，a dark room）
