FROM ubuntu:20.04 AS builderImage

ARG CPPCHECK_VERSION

RUN apt-get update
RUN apt-get install make g++ wget cmake -y
WORKDIR /home
RUN wget https://github.com/danmar/cppcheck/archive/refs/tags/$CPPCHECK_VERSION.tar.gz
RUN tar -xvzf $CPPCHECK_VERSION.tar.gz 
RUN mkdir /home/cppcheck-$CPPCHECK_VERSION/build
WORKDIR /home/cppcheck-$CPPCHECK_VERSION/build
RUN cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_EXE_LINKER_FLAGS=-static ..
RUN make install

FROM alpine:3.17.0
RUN mkdir -p /home/cppcheck
RUN mkdir /lib64 && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2
COPY --from=builderImage /usr/bin/cppcheck /usr/bin/cppcheck
COPY --from=builderImage /usr/share/Cppcheck /usr/share/Cppcheck
WORKDIR /home/cppcheck
CMD ["--enable=all", "--language=c++", "--std=c++20", "--output-file=cppcheck-output.txt", "."]
ENTRYPOINT ["cppcheck"]
