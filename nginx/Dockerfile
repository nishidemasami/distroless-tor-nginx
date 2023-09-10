FROM debian:12 as build

RUN apt update && \
  apt install nginx -y --no-install-recommends && \
  cp -a --parents /usr/share/nginx /opt && \
  cp -a --parents /var/log/nginx /opt && \
  cp -a --parents /var/lib/nginx /opt && \
  cp -aL --parents /var/run /opt && \
  cp -a --parents /etc/nginx /opt && \
  cp -a --parents /etc/passwd /opt && \
  cp -a --parents /etc/group /opt && \
  cp -a --parents /usr/sbin/nginx /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libcrypt.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libpcre2-8.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libssl.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libcrypto.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libz.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libc.so.* /opt

FROM gcr.io/distroless/base-nossl-debian12:latest
COPY --from=build /opt /

EXPOSE 80

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]