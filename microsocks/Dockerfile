FROM alpine:latest

WORKDIR /build

RUN apk add --no-cache build-base curl jq && curl -sSL $(curl -s https://api.github.com/repos/rofl0r/microsocks/releases/latest | jq -r '.tarball_url') |  tar xz --strip-components=1 && \ 
    make && mkdir /app && mv /build/microsocks /app/ && apk del build-base && rm -rf /var/cache/apk/* /build

WORKDIR /app

EXPOSE 1080

CMD ["/bin/sh", "-c", "/app/microsocks -1 -q -p 1080 -u ${USERNAME:-user} -P ${PASSWORD:-pass}"]
