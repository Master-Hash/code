# deno
Docker hub 上面已经有不少镜像了，不过我还是想自己构建一个。

需要注意，编译时不能使用 `rust:alpine` 镜像。

原因：上游未官方提供 musl 头文件。（见 [releases](https://github.com/denoland/deno/releases)）参考 [issue#3711](https://github.com/denoland/deno/issues/3711)

但也不是没有办法，比如可以照着这个 [gist](https://gist.github.com/kesor/68df53a5d76784a235ca6b0e7efed4d9)，不过我还是希望照着官方的支持来~

---
目前有两个已知问题：
- ~~`cargo install` 命令还不知道怎么改编译参数，所以不知道怎么缩小 bin 的大小；~~

`cargo install` 默认使用 release profile；[profile](https://github.com/denoland/deno/blob/master/Cargo.toml) 中已经指定了为体积优化的参数

参考：
- [优化 Rust 程序编译体积 - Aloxaf's Blog](https://www.aloxaf.com/2018/09/reduce_rust_size/)
- [GitHub - johnthagen/min-sized-rust](https://github.com/johnthagen/min-sized-rust)

不过我只加了 strip，别的需要改源码或者会改变程序行为的，我就不动了&zwnj;~~（我既不会 js，也不会 rust，真不知道打这个包干啥）~~

---
- ~~成品似乎是 static 的~~，不过还不清楚隐藏的 libc，etc 依赖。

然而并不是（  
实际上，需要的依赖有 `glibc`（[issue](https://github.com/deadlinks/cargo-deadlinks/issues/82)） `libgcc`（用 ldd 自己看看？），在 `debian:buster-slim` 镜像里预装。
