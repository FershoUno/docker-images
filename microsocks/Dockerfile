FROM alpine:latest

RUN apk add --no-cache build-base curl jq
WORKDIR /build

RUN curl -sSL $(curl -s https://api.github.com/repos/rofl0r/microsocks/releases/latest | jq -r '.tarball_url') |  tar xz --strip-components=1
RUN make
RUN mkdir /app && mv /build/microsocks /app/
RUN apk del build-base && rm -rf /var/cache/apk/* /build

WORKDIR /app
EXPOSE 1080
CMD ["/bin/sh", "-c", "/app/microsocks -1 -p 1080 -u ${USERNAME:-user} -P ${PASSWORD:-pass}"]
