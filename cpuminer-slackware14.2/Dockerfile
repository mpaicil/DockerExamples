from vbatts/slackware:14.2

maintainer Mauricio Paicil <mauricio.paicil.g@gmail.com>

run sed -i 's/BATCH=off/BATCH=on/' /etc/slackpkg/slackpkg.conf && sed -i 's/DEFAULT_ANSWER=n/DEFAULT_ANSWER=y/' /etc/slackpkg/slackpkg.conf && slackpkg update && slackpkg install gcc cmake automake perl libmpc python autoconf m4 git cyrus-sasl pkg-config libevent libtool binutils glibc kernel-headers make curl gpgme libassuan libgpg-error guile gc libffi libunistring && ldconfig && wget -d -c https://software.jaos.org/slackpacks/14.1-x86_64/slapt-get/slapt-get-0.10.2t-x86_64-1.tgz --no-check-certificate && wget -d -c https://software.jaos.org/slackpacks/14.1-x86_64/slapt-src/slapt-src-0.3.2i-x86_64-1.tgz --no-check-certificate && installpkg slapt-get-0.10.2t-x86_64-1.tgz slapt-src-0.3.2i-x86_64-1.tgz && git config --system http.sslverify false && sed -i 's/#SOURCE/SOURCE/' /etc/slapt-get/slapt-srcrc && sed -i 's/SOURCE=http:\/\/www.slackware/#SOURCE=http:\/\/www.slackware/' /etc/slapt-get/slapt-srcrc && sed -i 's/14.0/14.2/' /etc/slapt-get/slapt-srcrc && slapt-src -u && ldconfig && slapt-src -i jansson -y 
workdir /root/
run git clone https://github.com/hyc/cpuminer-multi.git
workdir /root/cpuminer-multi
run sh autogen.sh && ./configure CFLAGS="-O3" && make && slackpkg remove cmake make gcc git kernel-headers slapt-get slapt-src 

ENV WALLET empty
ENV POOL monerohash.com:3333

CMD ./minerd -a cryptonight -o stratum+tcp://$POOL -u $WALLET -p x
