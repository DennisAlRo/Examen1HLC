ARG AUTOR
FROM ${AUTOR}/nginx

ENV USUARIO="DARdennis"
ENV PASSWORD="DARdennis"
ARG CONTEXT
ARG PROYECTO
ARG TZ
ARG GITHUB


USER root
RUN apt update && apt install -yq --no-install-recommends \
    npm install

COPY ${GITHUB} /home/${USUARIO}/app 
RUN apt-get update && apt-get install -y curl gnupg software-properties-common

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash -

RUN apt-get install -y nodejs

RUN node --version && npm --version 

WORKDIR /root/admin/nginx
ENTRYPOINT ["./admin/start.sh"]