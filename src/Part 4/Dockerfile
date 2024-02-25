FROM nginx

RUN apt update && \
    apt install -y gcc libfcgi-dev spawn-fcgi

COPY ./server/server.c .
COPY ./nginx/nginx.conf /etc/nginx
COPY ./run.sh .

ENTRYPOINT ["bash", "run.sh"]