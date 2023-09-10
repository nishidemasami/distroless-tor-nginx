FROM debian:12 as build

RUN apt update && \
  apt install tor -y --no-install-recommends && \
  cp -a --parents /usr/bin/tor /opt && \
  cp -a --parents /usr/sbin/tor /opt && \
  cp -a --parents /etc/tor /opt && \
  cp -aL --parents /usr/share/tor /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libz.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libm.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libevent-2.1.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libssl.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libcrypto.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libsystemd.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/liblzma.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libzstd.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libseccomp.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libcap.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libc.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libgcrypt.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/liblz4.so.* /opt && \
  cp -a --parents /lib/x86_64-linux-gnu/libgpg-error.so.* /opt

FROM gcr.io/distroless/base-debian12
COPY --from=build /opt /

ENTRYPOINT  ["/usr/bin/tor"]