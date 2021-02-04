FROM rust:latest

WORKDIR /usr/local/cargo/bin

RUN cargo install deno \
 # 用于 debug
 && ls .

FROM busybox:glibc

COPY --from=0 deno /usr/local/bin

CMD [ "deno" ]
