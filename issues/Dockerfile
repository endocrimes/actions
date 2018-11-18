FROM golang:1.11 as builder

RUN go get github.com/endocrimes/gcli
RUN cd $GOPATH/src/github.com/endocrimes/gcli && go build -o gcli && cp gcli /gcli

FROM debian:stable-slim

LABEL "name"="issues"
LABEL "maintainer"="Danielle Tomlinson <dani+oss@builds.terrible.systems>"
LABEL "version"="0.0.1"

LABEL "com.github.actions.name"="Commands related to Issues for GitHub Actions"
LABEL "com.github.actions.description"="Common commands for managing issues"
LABEL "com.github.actions.icon"="filter"
LABEL "com.github.actions.color"="gray-dark"

COPY LICENSE.md README.md /

RUN apt-get update && \
    apt-get install --no-install-recommends -y \
        jq bash curl ca-certificates && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/*

ENV PATH="/usr/local/bin:${PATH}"

COPY bin /usr/local/bin/
COPY entrypoint.sh /entrypoint.sh

COPY --from=builder /gcli /usr/local/bin/filter

ENTRYPOINT ["/entrypoint.sh"]
