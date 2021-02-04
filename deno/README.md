# deno
Docker hub 上面已经有不少镜像了，不过我还是想自己构建一个。

需要注意，编译时不能使用 `rust:alpine` 镜像。

目前有两个已知问题：
- `cargo install` 命令还不知道怎么改编译参数，所以不知道怎么缩小 bin 的大小；
- 成品似乎是 static 的，不过还不清楚隐藏的 libc，etc 依赖。
