FROM nginx

RUN apt update && \
    apt install -y gcc libfcgi-dev spawn-fcgi && \
    rm -rf /var/lib/apt/lists && \ 
    useradd -ms /bin/bash dockeruser

COPY ./server/server.c .
COPY ./nginx/nginx.conf /etc/nginx
COPY ./run.sh .

USER dockeruser
WORKDIR /home/dockeruser

HEALTHCHECK --interval=5m --timeout=3s CMD curl -f http://localhost/ || exit 1

ENTRYPOINT ["bash", "run.sh"]