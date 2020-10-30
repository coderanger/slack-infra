FROM golang:1 as build

ADD . /src
WORKDIR /src

RUN go build -o /slack-moderator sigs.k8s.io/slack-infra/slack-moderator

FROM gcr.io/distroless/base
COPY --from=build /slack-moderator /slack-moderator
USER 65534
ENTRYPOINT ["/slack-moderator"]
