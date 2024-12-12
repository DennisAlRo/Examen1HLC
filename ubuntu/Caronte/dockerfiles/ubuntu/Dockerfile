FROM ubuntu:24.04
ENV USUARIO="DARdennis"
ENV PASSWORD="DARdennis"
# ENV CONTEXTO=${CONTEXTO}
ARG TZ
ARG CONTEXT
# ARG D_FILES=${CONTEXT}/dockerfiles
ARG PROYECTO
ARG AUTOR
USER root
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt update && apt install -yq --no-install-recommends \
    apt-utils \
    wget curl git \
    nano \ 
    tree \
    net-tools \ 
    iputils-ping \
    sudo \ 
    openssh-server \ 
    openssh-client \
    unzip \
    dos2unix \ 
    expect \
    python3

RUN mkdir /var/run/sshd
EXPOSE 22

RUN mkdir /root/logs
RUN mkdir /root/datos
RUN touch /root/logs/build.log
COPY ./common/id_rsa.pub /root/datos
RUN echo "contexto: ${D_FILES}" 

RUN mkdir /root/admin
COPY ./dockerfiles/ubuntu/admin /root/admin

RUN chmod +x /root/admin/start.sh
WORKDIR /root/admin

# RUN dos2unix /root/admin/start.sh 
ENTRYPOINT ["/etc/init.d/ssh start &"]